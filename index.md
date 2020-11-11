![]<img src="doc/landing.png">

Digits is an application that allows users to:

  * Register an account.
  * Create and manage a set of contacts.
  * Add a set of timestamped notes regarding their interactions with each contact.

### Installation

First, [install Meteor](https://www.meteor.com/install).

Second, go to [https://github.com/ics-software-engineering/meteor-application-template-react](https://github.com/ics-software-engineering/meteor-application-template-react), and click the "Use this template" button. Complete the dialog box to create a new repository that you own that is initialized with this template's files.

Third, go to your newly created repository, and click the "Clone or download" button to download your new GitHub repo to your local file system.  Using [GitHub Desktop](https://desktop.github.com/) is a great choice if you use MacOS or Windows.

Fourth, cd into the app/ directory of your local copy of the repo, and install third party libraries with:

```
$ meteor npm install
```

### Running the system

Once the libraries are installed, you can run the application by invoking the "start" script in the [package.json file](https://github.com/ics-software-engineering/meteor-application-template-react/blob/master/app/package.json):

```
$ meteor npm run start
```

The first time you run the app, it will create some default users and data. Here is the output:

```
C:\Users\cch48\Desktop\github\cheolhoonchoi\digits\app>meteor npm run start

> meteor-application-template-react@ start C:\Users\cch48\Desktop\github\cheolhoonchoi\digits\app
> meteor --no-release-check --exclude-archs web.browser.legacy,web.cordova --settings ../config/settings.development.json

[[[[[ C:\Users\cch48\Desktop\github\cheolhoonchoi\digits\app ]]]]]

=> Started proxy.
=> Started MongoDB.
W20201110-22:56:05.018(-10)? (STDERR) Note: you are using a pure-JavaScript implementation of bcrypt.
W20201110-22:56:05.193(-10)? (STDERR) While this implementation will work correctly, it is known to be
W20201110-22:56:05.195(-10)? (STDERR) approximately three times slower than the native implementation.
W20201110-22:56:05.196(-10)? (STDERR) In order to use the native implementation instead, run
W20201110-22:56:05.197(-10)? (STDERR) 
W20201110-22:56:05.200(-10)? (STDERR)   meteor npm install --save bcrypt
W20201110-22:56:05.203(-10)? (STDERR) 
W20201110-22:56:05.206(-10)? (STDERR) in the root directory of your application.
I20201110-22:56:08.865(-10)? Creating the default user(s)
I20201110-22:56:08.867(-10)?   Creating user admin@foo.com.
I20201110-22:56:09.486(-10)?   Creating user john@foo.com.
I20201110-22:56:09.999(-10)? Creating default data.
I20201110-22:56:10.002(-10)?   Adding: Johnson (john@foo.com)
I20201110-22:56:10.024(-10)?   Adding: Casanova (john@foo.com)
I20201110-22:56:10.027(-10)?   Adding: Binsted (admin@foo.com)
I20201110-22:56:10.141(-10)? Monti APM: completed instrumenting the app
=> Started your app.

=> App running at: http://localhost:3000/
   Type Control-C twice to stop.
```


### Note regarding "bcrypt warning":

You will also get the following message when you run this application:

```
Note: you are using a pure-JavaScript implementation of bcrypt.
While this implementation will work correctly, it is known to be
approximately three times slower than the native implementation.
In order to use the native implementation instead, run

  meteor npm install --save bcrypt

in the root directory of your application.
```

On some operating systems (particularly Windows), installing bcrypt is much more difficult than implied by the above message. Bcrypt is only used in Meteor for password checking, so the performance implications are negligible until your site has very high traffic. You can safely ignore this warning without any problems during initial stages of development.

### Note regarding "MongoError: not master and slaveOk=false":

Intermittently, you may see the following error message in the console when the system starts up:

```
MongoError: not master and slaveOk=false
     at queryCallback (/Users/philipjohnson/.meteor/packages/npm-mongo/.3.1.1.1mmptof.qcqo++os+web.browser+web.browser.legacy+web.cordova/npm/node_modules/mongodb-core/lib/cursor.js:248:25)
     at /Users/philipjohnson/.meteor/packages/npm-mongo/.3.1.1.1mmptof.qcqo++os+web.browser+web.browser.legacy+web.cordova/npm/node_modules/mongodb-core/lib/connection/pool.js:532:18
     at _combinedTickCallback (internal/process/next_tick.js:131:7)
     at process._tickDomainCallback (internal/process/next_tick.js:218:9)
```

While irritating, this message appears to be harmless and [possibly related to a race condition between the development instance of Mongo and Meteor](https://github.com/meteor/meteor/issues/9026#issuecomment-330850366). By harmless, I mean that in most cases, the console goes on to display `App running at: http://localhost:3000/` and no problems occur during run time.

### Viewing the running app

If all goes well, the template application will appear at [http://localhost:3000](http://localhost:3000).  You can login using the credentials in [settings.development.json](https://github.com/ics-software-engineering/meteor-application-template-react/blob/master/config/settings.development.json), or else register a new account.

### ESLint

You can verify that the code obeys our coding standards by running ESLint over the code in the imports/ directory with:

```
meteor npm run lint
```

### User Interface Walkthrough

The following sections describe the major features of this template.

## Landing page

When you retrieve the app at http://localhost:3000, this is what should be displayed:

![]<img src="doc/landing.png">

The next step is to use the Login menu to either Login to an existing account or register a new account.

## Login page

Clicking on the Login link, then on the Sign In menu item displays this page:

![]<img src="doc/logIn.png">

## Register page

Alternatively, clicking on the Login link, then on the Sign Up menu item displays this page:

![]<img src="doc/registerPage.png">

## Landing (after Login) page, non-Admin user

Once you log in (either to an existing account or by creating a new one), the navbar changes as follows:

![]<img src="doc/userPage.png">

You can now add new Stuff documents, and list the Stuff you have created. Note you cannot see any Stuff created by other users.

## Add Stuff page

After logging in, here is the page that allows you to add new Stuff:

![]<img src="doc/addPage.png">

## List Stuff page

After logging in, here is the page that allows you to list all the Stuff you have created:

![]<img src="doc/listPage.png">

You click the "Edit" link to go to the Edit Stuff page, shown next.

## Edit Stuff page

After clicking on the "Edit" link associated with an item, this page displays that allows you to change and save it:

![]<img src="doc/editPage.png">

## Landing (after Login), Admin user

You can define an "admin" user in the settings.json file. This user, after logging in, gets a special entry in the navbar:

![]<img src="doc/adminUser.png">

## Admin page (list all users stuff)

To provide a simple example of a "super power" for Admin users, the Admin page lists all of the Stuff by all of the users:

![]<img src="doc/adminPage.png">
