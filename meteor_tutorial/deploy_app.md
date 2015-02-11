# Deploy App

1) **Deploy to Meteor.com.**

Go to the command line (terminal) and type the following, replacing *my_app_name* with an application name of your choice. Follow the prompts to complete the process.

```
meteor deploy my_app_name.meteor.com
```
Go to the site *http://my_app_name.meteor.com* to view the deployed app.

# Notes

1) **Meteor Account:** To deploy at the default Meteor site, you will need a *Meteor.com* account. Setting one up is recommended since it is also used to publish packages to *atmospherejs.com* (the Meteor package repository), and allows for deployed app administration later.

2) **Mobile First:** Meteor is one of the platforms that is ideal for mobile-first design. Note how the developed web application is born mobile-ready and can be viewed on any modern browser on any device -- *with the real-time reactive capabilities intact*

3) **Deploy options:**

```
Usage: meteor deploy <site> [--settings settings.json] [--debug] [--delete]
```
Use 'meteor deploy' on command line to get more information on settings. Use the --delete option to delete or remove your hosted application from that site.

Deploying an application to an existing site overwrites or updates that application -- you are required to have permissions (i.e., via Meteor login) for that specific subdomain (site name) on meteor.com in order to do so.












