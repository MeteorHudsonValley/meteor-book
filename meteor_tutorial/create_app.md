# Create App

1)
**Change Directory** to the location where you want to create this new project.


2)
**Create boilerplate app** with the following command, where *simple-todos* is the name of the application being created.

```
meteor create simple-todos
```
This also creates a folder of the same name to hold the application contents.


3)
**Explore boilerplate** by changing to the app directory and listing contents.

```
cd simple-todos
ls -al

.meteor
simple-todos.css
simple-todos.html
simple-todos.js
```

4) **Run the application** from the command line.
```
meteor
```
This runs a webserver on the local host (on port 3000 by default).


5) **Verify the app is running** by visiting **http://localhost:3000** on your browser.

```
You should see a simple blank page with
  - a title (Welcome to Meteor!),
  - a small button (labelled *Click Me*)
  - a caption ("You've pressed the button 0 times.").
```


6)
**Test the application** by clicking the button. *Did the caption count get incremented? Its working!*


7)
**Try editing the code** (while the application is still running at command line). Ex: change the caption text or add a new element to the *simple-todos.html* file.


8)
**Save the changes**, and observe the application in the browser as you do so.

```
The browser app will update to show the changed view (caption or element)
You (the developer) didn't need to explicitly build, package or redeploy the code.
```
This automatic 'push' of code changes to running application sessions is a feature of Meteor, known as **hot code push.**



# Notes

1. **The .meteor folder**. Is created in the boilerplate project by default. It is meant for use by the  Meteor build/runtime system. Developers will rarely (i.e., never) need to edit it manually. *Take a minute and look at its contents*

2. **File Naming & Structure**. *Some* file names and locations have special significance in Meteor, particularly in terms of their loading order and their accessibility (at client, server, or both). This is critical to keep in mind as projects grow larger. *Look at the following: client/ server/ lib/ tests/ public/ private/ directories, and files named 'main'.*

3. **Meteor Commands.** Meteor development requires a basic text editor and a terminal, making the Meteor command line fairly critical to understanding and using Meteor effectively. *Take a minute to explore the command line menu options using the 'meteor --help' command. Then explore a specific command in depth using 'meteor help command' (e.g., 'meteor help run')*.


