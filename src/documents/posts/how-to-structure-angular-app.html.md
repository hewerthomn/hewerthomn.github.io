```
title: How to structure an AngularJS app
layout: post
tags: ['angular']
date: 2014-12-05
```

###***Working in progress...***###


Hello :D

After finished the [PhoneCat Tutorial](https://docs.angularjs.org/tutorial)
at the AngularJS docs I be worried how to structure an AngularJS app.
The app in tutorial is very simple and some components are included in a single
file like `controllers.js`.

This structure can't be a trouble if your app is very small, like the PhoneCat 
app, but as the app start to grow this aproach can be hard to maintain.

So I researched over the internet how I can structure my AngularJS app and some 
good practices to use.

** This is not a definitive guide and can be improved over time. **

In this tutorial I will show how to create an simple AngularJS app with this
structure.

Let's start! :D

### Setup dependencies

First we need to setup some dependencies tools to start the development.
If you already has installed nodejs, npm and bower jump to next section.

The first dependency to install is the [nodejs](http://nodejs.org/) 
(and npm if is not present).

After npm installed, we need to install the [bower](http://bower.io/) to
manage our font-end packages.

```
$ npm install -g bower
```
The param -g installs bower globaly to run the command in any directory.

To test if bower's working run the command `bower` in your terminal to see the
commands list.


### Folder structure

Create a folder to your project and enter there.

```
$ mkdir myapp && cd myapp
```

The basic folder structure can be like above.

You should add others folders if you need then, like `app/tests`, `app/scripts/providers`, etc.

```
myapp
--app
----scripts
--------controllers
--------directives
--------services
----views
--------directives
--------partials
--css
--img
```

To create this directories run the command above in your terminal:

```
mkdir -p app/scripts/controllers && mkdir app/scripts/directives && mkdir app/scripts/services && mkdir -p app/views/directives && mkdir app/views/partials && mkdir css && mkdir img
```

### Install the packages

I prefer to change the default directory of bower packages called `bower_components`
to `packages`, to do this I create a file at the root of
folder app called `.bowerrc` with the content:

```
{
  "directory": "packages"
}
```

Now we will install the AngularJS and the Twitter Bootstrap running the above
commands in your terminal:

```
bower install angular bootstrap
```

This single command will clone the AngularJS repository and the 
Twitter Bootstrap (and your dependency, the jQuery library) in the packages folder.
