---
layout: post
category:
tagline: ""
tags:
title: "A simple image carousel in Ember"
description: How to build a simple modal in Ember
author: vikram_ramakrishnan
---
{% include JB/setup %}

# Blog Post Outline [DRAFT]

## There are so many libraries out there that do carousels. Why do we need to write our own?!

You know image carousels:

![alt](http://i.imgur.com/KbJoa8K.gif)

They're tools that let a user loop through a series of pictures, either automatically or by clicking on some kind of indicator for a picture.

Now, there are tons of examples of these in JQuery: [Jssor](www.jssor.com/), which the above gif was drawn from, [Owl Carousel](owlgraphic.com/owlcarousel), [Slick.js](http://kenwheeler.github.io/slick/) and many, many others. That's great, right? We can just grab a library and slap it into our app and we're good, right?

Well, before we do that let's ask ourselves if we really need to do that. All of those JQuery libraries are excellent tools, but do we need them if our front end is Ember?

#### Stop using JQuery libraries for things Ember lets you do for free!

- Why do we want to do this?
- What does Ember give us?
- This is what ours will look like (animated gif)

## Alright, I'm convinced! How are we going to do this?

- First off, we'll need some kind of backend (do we?) and I don't think this worth spinning up a whole rails api or anything for this. We can look at Mirage. Don't want to get into all the details of Mirage (here are some blog posts), but we can get it setup and go with it.
- Pseudo-english-ed version of how we'll build this; why flow control will be important
- Addons we'll need for this project: font awesome & sass & mirage & ember truth helpers

## Is there anything conceptually that would help us out here?

- pod structure
- promises

## Implementation

Let's `ember new` our app from the command line:

`ember new image-carousel-example`

Now, let's `cd image-carousel-example` and add the dependencies to our app:

**Font Awesome**: [Ember CLI Font Awesome](https://github.com/lfridael/ember-cli-font-awesome)

```
ember install ember-cli-font-awesome
ember generate ember-cli-font-awesome
```

**Sass**: [Ember CLI Sass](https://github.com/aexmachina/ember-cli-sass)

```
npm install --save-dev ember-cli-sass
```

**Mirage** [Mirage](https://github.com/samselikoff/ember-cli-mirage)

```
ember install ember-cli-mirage
```

Run `npm install && bower install` to make sure all our dependencies are installed.

Ok, we've got our Ember app ready and its base dependencies installed.

Let's update our `app/router.js` file to handle the profile paths we'll care about:

```javascript
//app/router.js

import Ember from 'ember';
import config from './config/environment';

var Router = Ember.Router.extend({
  location: config.locationType
});

Router.map(function() {
  this.route('profiles');
  this.route('profile', { path: '/profiles/:profileId' });
});

export default Router;
```

Now let's update the `mirage` folder so there is a fake "backend" for our app:

```javascript
//app/mirage/config.js

export default function() {
  this.get('/profiles');
  this.get('/profiles/:id');
}
```

A factory for the profile:

```javascript
//app/mirage/factories/profile.js (renamed default contact.js)
import Mirage/*, {faker} */ from 'ember-cli-mirage';

export default Mirage.Factory.extend({
  name: faker.list.cycle('Fry', 'Bender', 'Leela', 'Zoidberg'),
  imageUrl: faker.list.cycle(
    'http://i.imgur.com/RYSCYTy.jpg',
    'http://i.imgur.com/n0LAiay.jpg',
    'http://i.imgur.com/0j3cEnX.jpg',
    'http://i.imgur.com/P3GptOE.jpg'
  )
});
```

Now we'll have our Mirage "server" create a list of four profiles for us to interact with:

```javascript
//app/mirage/scenarios/default.js

export default function(server) {
  server.createList('profile', 4);
}
```

- code

## While we're at it, let's write some tests for this

## Stuff to try out

- Add animations! (check out liquidfire)
