# Authentication: Warden

1. Add gems

  ```
  gem 'warden'
  gem 'bcrypt'
  ```

2. Connect Warden

  The following enables you to access the Warden object via `params.env['warden']`.

  You can either add Warden at the Rack level:

  ```ruby
  # config.ru
  use Rack::Session::Cookie, secret: ENV['COOKIE_SECRET']

  use Warden::Manager do |manager|
    # let Hanami deal with the 401s
    manager.intercept_401 = false
  end
  ```

  or in an application:

  ```ruby
  module Web
    class Application < Hanami::Application
      configure do
        middleware.use Rack::Session::Cookie, secret: ENV['COOKIE_SECRET']

        middleware.use Warden::Manager do |manager|
          # let Hanami deal with the 401s
          manager.intercept_401 = false
        end
      end
    end
  end
  ```

  Note that if you use the latter and you want to share sessions between applications, you need to use the same secret.

3. Set up Warden strategies

  ```ruby
  # config/initializers/warden.rb
  Warden::Strategies.add(:password) do

    def valid?
      params['username'] || params['password']
    end

    def authenticate!
      u = User.authenticate(params['username'], params['password'])
      u.nil? ? fail!("Could not log in") : success!(u)
    end
  end

  Warden::Manager.serialize_into_session do |user|
    user.id
  end

  Warden::Manager.serialize_from_session do |id|
    User[id]
  end
```

4. Modify user model

  ```ruby
  require 'bcrypt'

  class User < Sequel::Model
    include BCrypt

    def password
      @password ||= Password.new(password_hash)
    end

    def password=(new_password)
      @password = Password.create(new_password)
      self.password_hash = @password
    end

    def self.authenticate(username, password)
      user = self.first(email: username)
      if !user.nil? && user.password == password
        return user
      end
      nil
    end
  ```

5. Authenticate the user

  ```ruby
  # this is a POST action
  class Login
    include Web::Action
    include Hanami::Action::Session

    def call(params)
      if params.env['warden'].authenticate(:password)
        redirect_to routes.logged_in_path
      else
        flash[:message] = 'Invalid credentials.'
        redirect_to routes.login_path
      end
    end
  end
  ```

## Notes

* Once authenticated, you can access the Warden user object via `params.env['warden'].user`.
* This was written by using Sequel rather than Hanami::Model. Adjust the `User[id]` call in the strategy and a few other places accordingly.
