# Collections

[Collections](http://docs.meteor.com/#/basic/Mongo-Collection) are the default Meteor way of storing persistent data (in a database). The term is inspired by[ MongoDB ](http://www.mongodb.org) usage, with Mongo being the default database supported in Meteor today.

Collections are accessible *using the same API* from both client and server, giving the developer a consistent way to view or update that data from anywhere.

This is achieved using [DDP (Distributed Data Protocol)](https://www.meteor.com/ddp) which keeps a client-side *in-memory database cache* synched with the server-side *master database*, such that a client-side automatically accesses only the most up-to-date data.

**1) Create Collection.** Update *simple-todos.js* as follows:

```
// simple-todos.js
Tasks = new Mongo.Collection("tasks");

if (Meteor.isClient) {
  // This code only runs on the client
  Template.body.helpers({
    tasks: function () {
      return Tasks.find({});
    }
  });
}
```
Save the changes. You'll notice the live application updates to show an empty list of tasks.

Why? Because the list is now bound

2) **Add Collection Data**.

Add data directly into the MongoB database as follows:

```
$ meteor mongo
MongoDB shell version: 2.4.12
connecting to: 127.0.0.1:3001/meteor

meteor:PRIMARY> show databases
local	0.0625GB
meteor	(empty)

meteor:PRIMARY> db.tasks.insert({ text: "Hello world!", createdAt: new Date() });
```

Observe the app in the browser. It should live update with the inserted data.


# Notes
