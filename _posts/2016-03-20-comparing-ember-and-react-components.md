---
layout: post
title: "Comparing Ember and React Components"
description: ""
category: 
tags: []
---
{% include JB/setup %}

# Comment Box

Fridays here at Greenfield are personal improvement days. We spend the day
working on something of our own choice that will help us grow as developers. We
spent part of a recent Friday going through the [React Tutorial] as a team.
Since we're all [Ember] developers, this lead to us making lots of comparisons.

## Getting Started

We're going to use [ember-cli] to set up our app. This won't provide us with a
local API server to run like like in the source files provided by the React
tutorial but we'll another tool to handle that later on.

If you don't already have [ember-cli] installed, head over to [Installing
Ember][installing-ember].

To get started, we're going to use ember-cli to generate our new Ember app:

```javascript
ember new ember-comment-box
```

Now we can start the local ember app and view it in our browser at
[http://localhost:4200](localhost):

```bash
cd ember-comment-box
ember server
```

## Your First Component

> React is all about modular, composable components

Great! So is Ember.

To recap what the component structure that we're going to be building looks
like, it's this:

```no-highlight
- CommentBox
  - CommentList
    - Comment
  - CommentForm
```

The first version of our `CommentBox` component only needs to display some text.
Since there's no logic required yet, we only need to create a template:

```handlebars
// app/templates/components/comment-box.hbs

Hello, world! I am a comment-box.
```

Now we can use our new component inside our `application.hbs` template:

```handlebars
// app/templates/application.hbs

{{comment-box}}
```

--- compare JSX and Handlebars ---

## Composing Components

Let's build skeletons for `{{comment-list}}` and `{{comment-form}}` components:

```handlebars
// app/templates/components/comment-list.hbs

Hello, world! I am a CommentList.
```

```handlebars
// app/templates/components/comment-form.hbs

Hello, world! I am a CommentForm.
```

Now we can use these new components inside our `{{comment-box}}` component:

```handlebars
// app/templates/components/comment-box.hbs

<h1>Comments</h1>
{{comment-list}}
{{comment-form}}
```

### Using Props

- Task: Create a `{{comment-list-item}}` component
- Task: Pass data from parent component to child `{{comment-list-item}}`
  component

In React, data passed to a component is available inside the component via
`this.props`. Ember handles this a little bit differently, setting data passed
to a component as properties directly on the component.

In a template, we can access any properties that are available on the
component:

NOTES: update the {{comment-list-item}} template to match

--- add info about why we need to use {{comment-list-item}} vs {{comment}} ---

```handlebars
// app/components/templates/comment-list-item.hbs

<h2>{{author}}</h2>

{{yield}}
```

--- explain yield ---

Now that we have our `{{comment-list-item}}` component, we can use it to display
some comments on the page:

```handlebars
// app/templates/components/comment-list.hbs

{{#comment-list-item author="Yehuda Katz"}}
  This is one comment
{{/comment-list-item}}

{{#comment-list-item author="Tom Dale"}}
  This is *another* comment
{{/comment-list-item}}
```

--- explain block form of the component && yield ---

### Adding Markdown

Just like in the React tutorial, we're going to use a 3rd party library,
[ember-markdown-it][ember-markdown-it] to convert our Markdown text to HTML.

Install the ember-markdown-it ember addon:

```bash
ember install ember-markdown-it
```

We can update our `{{comment-list-item}}` component to convert the Markdown
content it yields as HTML:

```handlebars
// app/templates/components/comment-list-item.hbs

// update this to use ember-markdown-it
{{#markdown-convert}}
  {{yield}}
{{/markdown-convert}}
```

### Hook Up the Data Model

- Task: Render comments from a blob of JSON data


[react-tutorial]: https://facebook.github.io/react/docs/tutorial.html
[installing-ember]: https://guides.emberjs.com/v2.4.0/getting-started/
[localhost]: http://localhost:4200
[ui-markdown]: https://github.com/lifegadget/ui-markdown
