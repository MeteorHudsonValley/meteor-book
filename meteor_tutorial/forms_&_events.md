# Forms and Events

**1) Add a form**.

Modify *simple-todos.html* to add the form element below.

```
<header>
  <h1>Todo List</h1>

  <!-- add a form below the h1 -->
  <form class="new-task">
    <input type="text" name="text" placeholder="Type to add new tasks" />
  </form>
</header>
```

The app should now have an input field to enter new tasks. Enter something here. *Nothing happens. Text disappears. Why? No event handling yet.*

**2) Handle form events.**

Modify *simple-todos.js* to handle the 'submit' event from the form.

```
Template.body.events({
  "submit .new-task": function (event) {
    // This function is called when
    // the new task form is submitted

    var text = event.target.text.value;

    Tasks.insert({
      text: text,
      createdAt: new Date() // current time
    });

    // Clear form
    event.target.text.value = "";

    // Prevent default form submit
    return false;
  }
});
```
Now try task entry again.

*The onscreen list should now show the new task added. And, the database 'tasks' collection should show an updated count as well.*

**3) Sort Tasks In List.**
Modify *simple-todos.js* to add the sort option to the Tasks.find() query.

```
Template.body.helpers({
  tasks: function () {
    // Show newest tasks first
    return Tasks.find({}, {sort: {createdAt: -1}});
  }
});
```
Save. *The task list should now be sorted to show most recently added tasks first.*

# Notes

1. **Suppress Default Action.** Note that event handler returns *false* to let browser know that this event has been handled, and that the browser's default submit action should not be executed.
