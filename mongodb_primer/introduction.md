# Getting Started

### 1. **Install MongoDB**.
Just follow the instructions for your specific device OS [from this link](http://docs.mongodb.org/manual/installation/). *I currently use [Mac OS X](http://docs.mongodb.org/manual/tutorial/install-mongodb-on-os-x/). My notes reflect usage of environment. YMMV.*

### 2. **Run MongoDB**.
Verify that your install is correct by running the MongoDB server on your local machine [as described here](http://docs.mongodb.org/manual/tutorial/install-mongodb-on-os-x/#run-mongodb). Make sure that the local PATH is set to include the location of the *mongod* and *mongo* binaries from this distribution.

```
mkdir -p /data/mydb        --> identify local db location
chmod u=rwx /data/mydb     --> give user read/write access to db

mongod --dbpath /data/mydb --> run the Mongo daemon
```

At this point, the *mongodb* database server (daemon) is running.


### 3. **Run the Mongo Console**.
Use the *mongo* utility to connect to the *mongodb* server and open a shell for interactions.

```
mongo
MongoDB shell version: 2.6.4
connecting to: test
>
```
You should see the above output, followed by a prompt for commands.

The *mongo* shell is a powerful, interactive interface for viewing, querying and maintaining all MongoDB databases on the connected server. Check this page for [a comprehensive reference to the *mongo* shell commands](http://docs.mongodb.org/manual/reference/mongo-shell/).

Explore available menu options with the 'help' command.
```
> help
	db.help()                    help on db methods
	db.mycoll.help()             help on collection methods
	sh.help()                    sharding helpers
	rs.help()                    replica set helpers
	help admin                   administrative help
	help connect                 connecting to a db help
	help keys                    key shortcuts
	help misc                    misc things to know
	help mr                      mapreduce display on shell
	....

	exit                         quit the mongo shell
>
```
You can quit the shell at any time with *exit.*

### 4. **Quick Commands**

For convenience, here are the most frequently used shell commands.

* **db** = show currently active db
* **show databases** = show all (non-empty) dbs on this server
* **show collectios** = show all collections in current db
* **use mydb** = make 'mydb' the current (active) db
* **db.help()** = list all methods that can be called on db
* **db.createCollection('myColl')** = create the 'myColl' collection on current db
* **db.showCollections()** = show all collections in current db
* **db.dropDatabase()** = delete the db

The following commands are used on a specific collection (where **myColl** should be replaced by the appropriate collection that you are running these commands on)

* **db.myColl.help()** = list all methods that can be called on this collection
* **db.myColl.drop()** = delete this collection
* **db.myColl.dropIndexes()** = delete a specific index on this collection
* **db.myColl.getDB()** = get the db object associated with this collection

This is a list of frequently used commands for basic CRUD (create, read, update, delete) operations that most applications require.

* **db.myColl.count()** = returns number of documents in this collection
* **db.myColl.insert(obj)** = inserts the specified document (obj) in this collection (, creating the collection if non-existent)
* **db.findOne(query)** = find one (the first) document matching the query.
* **db.myColl.find(query)** = find all matching documents in the collection (returns [cursor](http://docs.mongodb.org/manual/core/cursors/#read-operations-cursors), which is transient. To get data as well, use *.find().fetch()* in Meteor only)
* **db.myColl.update(query, object[.., upsert_flag, multi_flag])** = updates the document(s) selected by the query with the data in the object. If upsert_flag is true, this will insert the document if it did not exist a priori. If multi_flag is true, it updates *all* matching documents for query (not just the first match).
* **db.myColl.remove(query)** = remove all documents matching the query. Note that if query is an empty document ({}), this removes *all* documents in collection. This is different from *dropping* the collection since this approach retains indexes.


# Notes


