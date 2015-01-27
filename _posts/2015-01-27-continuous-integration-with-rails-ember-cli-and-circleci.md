---
layout: post
title: "Continuous Integration with Rails, Ember CLI, and CircleCI"
description: "How to set up continuous integration for a Rails and Ember CLI application."
category:
tags: [rails, ember-cli, CircleCI, continuous-integration]
author: Eric Kelly
---
{% include JB/setup %}

Services like [CircleCI][circle] and [Travis CI][travis] make it really
straight forward to get set up with [continuous
integration][continuous-integration] for a single application. When you have
both a [Rails][rails] and [Ember CLI][ember-cli] application living in single
repository, it requires a little bit of customization.

This assumes that you're using:

- CircleCI
- Rails & RSpec
- Ember CLI & the default test setup with [ember-cli-qunit][ember-cli-qunit]

## The Repository Structure

├── README.md
├── circle.yml
├── ember
│   ├── app
│   ├── config
│   ├── dist
│   ├── misc
│   ├── public
│   └── tests
└── rails
    ├── app
    ├── bin
    ├── config
    ├── db
    ├── lib
    ├── log
    ├── public
    ├── spec
    ├── tmp
    └── vendor

## circle.yml

```yml
general:
  # Use Circle CI's automatic settings inference for the Rails app
  build_dir: rails
dependencies:
  # Install Ember CLI dependencies after those for Rails
  post:
    - cd ../ember && npm install
    - cd ../ember && bower install
  # Cache the Ember CLI dependencies to speed up future builds
  cache_directories:
    - "../ember/node_modules"
    - "../ember/bower_components"
test:
  # Run the Ember tests after the Rails tests
  post:
    - cd ../ember && ./node_modules/.bin/ember test
```

## Environment Variables

I recommend checking out the [dotenv][dotenv] and
[ember-cli-dotenv][ember-cli-dotenv] projects if your application requires the
use of environment variables for configuration. You can easily set these up on
the Circle CI through their web interface.

## Additional Steps

If your build process requires any further configuration, check out the [Circle
CI Documentation][circle-ci-docs]. They also have a really helpful chatroom set
up where you can get easily ask for additional help.

[circle-ci-docs]: https://circleci.com/docs "Circle CI Documentation"
[circle]: https://circleci.com/ "CircleCI"
[continuous-integration]: http://en.wikipedia.org/wiki/Continuous_integration "Continuous Integration"
[dotenv]: https://github.com/bkeepers/dotenv "dotenv"
[ember-cli-dotenv]: https://github.com/fivetanley/ember-cli-dotenv "Ember CLI dotenv"
[ember-cli-qunit]: https://github.com/ember-cli/ember-cli-qunit "Ember CLI QUnit"
[ember-cli]: https://github.com/ember-cli/ember-cli "Ember CLI"
[rails]: http://rubyonrails.org/ "Ruby on Rails"
[travis]: https://travis-ci.org/ "Travis CI"
