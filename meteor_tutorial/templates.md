# Templates

So far, we've seen the basic boilerplate application code. Now its time to customize it for our application.

**1) Modify View: ** Update the *simple-todos.html*  file as specified [in this step](https://www.meteor.com/try/2).

```html
<head>
  <title>Todo List</title>
</head>

<body>
  <div class="container">
    <header>
      <h1>Todo List</h1>
    </header>

    <ul>
      {{#each tasks}}
        {{> task}}
      {{/each}}
    </ul>
  </div>
</body>

<template name="task">
  <li>{{text}}</li>
</template>
```
Note that the HTML has only *head*, *body* and *template* elements (no *html* enclosing root element).


**2) Modify Behavior:** Update the *simple-todos.js* file as specified [in this step](https://www.meteor.com/try/2).

```js
// simple-todos.js
if (Meteor.isClient) {
  // This code only runs on the client
  Template.body.helpers({
    tasks: [
      { text: "This is task 1" },
      { text: "This is task 2" },
      { text: "This is task 3" }
    ]
  });
}
```
Note that at this point, all files are still in the same directory (no separation into client/, server/ folders) meaning that the contents are *technically* made available to both endpoints.

However, the *Meteor.isClient* conditional acts as a scope, identifying the enclosed code as being relevant to client side only. Meteor uses this when packaging the subset of the codebase that is intended for client-side deployment (i.e., pushed or downloaded to the client device).

**3) Deploy Changes.** Save the changed files. If your application was already running, it is updated by a hot code push. Else, run the application again from commandline (using 'meteor').

```
You should see a list titled "Todo List" with three items.
Each item will be in the form "This is task <1>"
```

** 4) Modify Styles.** Update the *simple-todos.css* file as specified [in this step](https://www.meteor.com/try/2).
(The contents are not shown here for clarity of discussion)

Save the changed files and wait for hot code push to complete. You should see a significant change in the UI presentation.


# Notes

1. **HTML files define 'templates'.** A template is a 'blueprint' for an HTML snippet with placeholders where relevant data can be 'bound' at runtime (e.g., by evaluating an expression, running a query etc.). In Meteor, a template must be declared with a unique name (as *template name="task"*) before it can be used in an HTML view (as *{{> task}}*) or referenced in JavaScript (as Template.*task*) for data binding or event handling.
**Note:** The "body" element is considered a template by default, accessible as Template.*body* from JavaScript.

2. **Templating Language.** A templating language provides special semantics that can be processed by a templating engine to "initialize" (the data) or "render" (a view of) that template. Examples are [Handlebars](http://handlebarsjs.com/), [Jade](http://jade-lang.com/reference/) and Meteor's own [Spacebars](https://github.com/meteor/meteor/blob/devel/packages/spacebars/README.md) (inspired by Handlebars). Special semantics can support

3. **Reactive Templating Engine (RTE).** A template rendering engine 'stamps' out templates (i.e., initializes them with data) and uses them to compose the UI body. A *reactive* templating engine takes this a step further by detecting changes to that bound data at runtime, and automatically updating the view in response.

4. **Blaze Reactive Templating Engine.** [Blaze](https://www.meteor.com/blaze) is Meteor's newly-rewritten RTE.
(Server-side) Blaze is a *template compiler* that uses [Spacebars](https://github.com/meteor/meteor/blob/devel/packages/spacebars/README.md) to convert templates into JavaScript code which gets included in the 'app.js' downloaded to clients. (Client-side) Blaze is a *reactive DOM engine* that registers & initializes templates, renders & injects the 'body' into DOM -- then uses [Tracker](https://www.meteor.com/tracker) (previously Deps) to detect changes to template data bindings, and reactively updates the UI to show the latest state.

5. **Template Helpers.** allow data to be passed (bound) between JavaScript and HTML at runtime. In particular, any variables (functions, objects) declared in the Template.*name*.helpers object are now transparently accessible (or bound) to similar-named variables found in "{{ }}"-enclosed expressions in the HTML for that named template. *Ex: above, Template.body.helpers({tasks: [..]}) effectively binds to the 'tasks' variable used in the {{#each tasks}} expression within the corresponding 'body' HTML. Since tasks has 3 array elements, it now causes the #each to iterate over that loop three times, passing 1 array element (containing the 'text' variable) as the default 'this' object for that iteration. Within an iteration, the '{{text}}' expression expects to see a 'this.text variable containing the relevant data for that list item -- and because of the Template.helpers binding, it does.*

6. **Recommended Reading**.
    - [A Look at a Meteor Template ](https://www.discovermeteor.com/blog/a-look-at-a-meteor-template/) (**Feb 2013**, Discover Meteor Blog)
    - [A Guide To Meteor Templates and Data Contexts](https://www.discovermeteor.com/blog/a-guide-to-meteor-templates-data-contexts/) (**Apr 2014**, Discover Meteor Blog)
    - [Spacebars Secrets: Exploring Meteor Templates](https://www.discovermeteor.com/blog/spacebars-secrets-exploring-meteor-new-templating-engine/) (**May 2014**, Discover Meteor Blog)
    - [How Blaze Works - Meteor's Reactive Templating UI](https://meteorhacks.com/how-blaze-works.html) (**August 2014**, MeteorHacks)
