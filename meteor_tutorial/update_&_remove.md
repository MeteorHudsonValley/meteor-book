# Update

1.** Update UI.**

Modify *simple-todos.html* to add new elements (checkbox, delete button) to the UI.

```
<!-- replace the existing task template with this code -->
<template name="task">
  <li class="{{#if checked}}checked{{/if}}">
    <button class="delete">&times;</button>

    <input type="checkbox" checked="{{checked}}" class="toggle-checked" />

    <span class="text">{{text}}</span>
  </li>
</template>
```

Save the file. *The form should update to show checkboxes and delete options on each list item. Ticking a checkbox, or clicking the delete button, should not do anything yet.*

2.** Handle Events.**

Modify *simple-todos.js* to add the event handlers.

```
// In the client code, below everything else
Template.task.events({

  "click .toggle-checked": function () {
    // Set the checked property to the opposite of its current value
    Tasks.update(this._id, {$set: {checked: ! this.checked}});
  },

  "click .delete": function () {
    Tasks.remove(this._id);
  }

});
```


# Notes

1) **Template Event Handlers:**. Note that since these interactive elements are in the *task* template, we invoke the  *Template**.task.**events* method and pass it a dictionary of event handlers, each providing a handler function for a named event type.

2) **Event Scope:** Also note that a template typically has access to *all* events in its section of the document. This includes events from its children. The template can choose to handle or ignore these events as appropriate. *Ex: Add a handler for the 'click' event in the body template event handler method, and log a message to console. Note how the message appears when the task template checkbox or delete functions are clicked.*

3) **MongoDB Operators:** The [MongoDB Reference](http://docs.mongodb.org/manual/reference/operator/) is a useful lookup to have at this point.
* **(Key)** Every MongoDB document has a unique identifier (*_id*); when a document is bound to a value in a template (e.g., each 'task' is a document from the Tasks collection), this *_id* is transparently accessible as *this._id*.
* **(Find)** runs a query on the collection and returns a 'cursor' to the results.
* **(Update)** runs a query with the given criteria, then updates one (multi=false) or all (multi=true) matching results according to the supplied data command.
* **(Remove)** runs a query with the given criteria and deletes all matching results.

4) **Reactive CSS.** Note the use of *{{#if checked}} checked {{/if}}* to conditionally add the 'checked' class to the list item. Templates helpers are reactive by default, allowing the UI to change automatically (e.g., its style) with changes to bound state/data.
