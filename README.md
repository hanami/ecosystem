# Hanami Ecosystem
This repository will include guides and documentation for integrating projects
from the Ruby ecosystem into Hanami.

## Mission
We strive to make Hanami a good Ruby citizen.

This means we want to ensure common libraries work well with Hanami,
*and* it also means that we want to ensure that Hanami works well with others too!

## Guides to write and publish
### Authentication
  - [ ] `warden`
  - [ ] [`rodauth`](https://github.com/davydovanton/hanami-rodauth) (@davydovanton)
  - [ ] `omniauth` (@davydovanton)

### Authorization
  - [ ] `cancancan`
  - [ ] `pundit`? (depends on ActiveSupport)
  - [ ] `authority`? (depends on ActiveSupport)

### Testing
  - [ ] [`rspec-hanami`](https://github.com/davydovanton/rspec-hanami) (@davydovanton)
  - [ ] `vcr` (@davydovanton)
  - [ ] `webmock`
  - [ ] `database_cleaner`

### API's
  - [ ] API documentation
  - [ ] JSON responses
    - [ ] [`jbuilder`](https://github.com/vladfaust/hanami-jbuilder)
    - [ ] `roar`
  - [ ] [JSON API™](https://github.com/jsonapi-rb/jsonapi-hanami) (@beauby)

### File Uploads
  - [ ] AWS S3, directly (@beauby)
  - [ ] shrine (https://github.com/katafrakt/hanami-shrine)

### Assets
  - [ ] hanami-assets (including limitations)
  - [ ] webpack (@davydovanton)
  - [ ] [bootstrap](https://github.com/davydovanton/hanami-bootstrap) (@davydovanton)
  - [ ] front-end frameworks, mention by name React, Ember, Angular, Elm, Vue, etc. (@davydovanton)

### Server hosting
  - [ ] logging
  - [ ] deploying
  - [ ] server monitoring

### Background jobs
  - [ ] `sidekiq`
  - [ ] `resque`

### Multiple language support
  - [ ] `i18n`

### Rack-compatibility
  - [ ] Mounting Hanami into other Rack-compatible frameworks
  - [ ] Mounting other Rack-compatible frameworks into Hanami

### Architecture tips
  - [ ] `Hanami::Interactor` (@davydovanton & @cllns)
  - [ ] `Hanami::Presenter`
  - [ ] Trailblazer (@apotonick?)
  - [ ] `dry-rb` libraries

### Real-time web
  - [ ] web sockets

### Alternative ORM's
  - [ ] `rom` (directly)
  - [ ] `sequel`?
  - [ ] `mongoid`?

### Others
  - [ ] email preview (@davydovanton)
  - [ ] URL slugs
  - [ ] pagination
  - [ ] state machines (@davydovanton?)
  - [ ] request throttling (rack-attack?)
  - [ ] A/B testing?
