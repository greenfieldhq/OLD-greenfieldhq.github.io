---
layout: post
category :
tagline: ""
tags : [ember, ember-cli, redactor]
title: "Redactor Ember component with Ember CLI and a Rails 4.1 backend"
description: How we created our Redactor component for Ember
author: Ryan Tremaine
---
{% include JB/setup %}

This blog post assumes you have a decent level of familiarity with Ember, Ember CLI, and Rails.

##Prerequisites
1. [Ember CLI 0.0.40](http://www.ember-cli.com/)
1. [Rails 4.1.0](http://rubyonrails.org/)
1. [Redactor 9.2.6+](http://imperavi.com/redactor/)

You might be fine with using slightly different versions of the prerequisites but these are the exact versions we used at the time of this writing.

##Setup and run!
1. `git clone git@github.com:greenfieldhq/ember-cli-redactor.git`
1. `cd ember-cli-redactor`
1. `cd ember`
1. `bower install`
1. `ember server --proxy http://localhost:3000`
1. In a new shell `cd ember-cli-redactor/rails`
1. `bundle install`
1. `rake db:migrate`
1. `rails s -p 3000`
1. Open a browser to http://localhost:4200 and you should see the running app and be able to create and edit documents

Directory structure

TODO: outro, future post on adding image support
