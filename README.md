# Hanami Ecosystem
This repository will include guides and documentation for integrating projects
from the Ruby ecosystem into Hanami.

## Mission
We strive to make Hanami a good Ruby citizen.

This means we want to ensure common libraries work well with Hanami,
*and* it also means that we want to ensure that Hanami works well with others too!

## Setup

### Requirements

  * Ruby 2+
  * Bundler (`gem install bundler`)

### Steps

```shell
% git clone git@github.com:hanami/hanami.github.io.git
% cd hanami.github.io
% bundle
```

## Command line

```shell
% bin/site help

Usage:
  bin/site [command]
Available commands:
  develop - Start the local server to develop the site
  build   - Build the site locally
  publish - Build the site locally and publish
  help    - Print this help
```

NOTE: There is an issue in which invoking `site` command with specified
current directory, `./bin/site` won't publish the site correctly. Please
invoke without `./`

## Production deployment

The deployment is automated with Travis CI. Upon merging PR into `build` branch, deployment script is invoked.

For more details, please consult `.travis.yml` file.
