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

---

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

--- 

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

--- 

### Install the packages

I prefer to change the default directory of bower packages called `bower_components`
to `packages`, to do this I create a file at the root of
folder app called `.bowerrc` with the content:

``` javascript
{
  "directory": "packages"
}
```

Now we will install the AngularJS running the above commands in your terminal:

```
bower install angular angular-route
```

This single command will clone the AngularJS repository and the package angular-route in the packages folder.

---

### Create the index page

I added the Yeti bootstrap theme for the UI and a custom style css. The ng-view directive is the place that our views will be rendered. After the ng-view directive, I included the angular file and the package angular-route, if you used the default directory of bower, the path will start with `bower_components/`.

*index.html*
``` html
<!DOCTYPE html>
<html ng-app="app" lang="en">
<head>
	<meta charset="UTF-8">
	<title>Repository Finder</title>

	<link rel="stylesheet" href="css/bootstrap-yeti.css">
	<link rel="stylesheet" href="css/style.css">
</head>
<body>

	<div ng-view class="container-fluid"></div>

	<footer class="container-fluid text-center text-muted">
		<hr>
		<small>Repository Finder</small>
	</footer>
	
	<!-- libraries -->
	<script src="packages/angular/angular.js"></script>
	<script src="packages/angular-route/angular-route.js"></script>

	<!-- app scripts -->
	<script src="app/scripts/controllers/main.js"></script>
	<script src="app/scripts/controllers/HomeCtrl.js"></script>
	<script src="app/scripts/app.js"></script>
</body>
</html>
```

---

The file `app/scripts/app.js` is where we setup de application. Here we define the modules used and configure the global settings of the app, like the routes.
The `app/scripts/controllers/main.js` is only to create the *app.controllers* module. Next, the file `app/scripts/controllers/HomeCtrl.js` has a empty controller in a Immediately-invoked function expression ([IIFE](http://en.wikipedia.org/wiki/Immediately-invoked_function_expression)).

*app/scripts/app.js*
``` javascript
angular.module('app', [
	'ngRoute',

	'app.controllers'
])
.config(['$routeProvider', function($routeProvider) {

	$routeProvider
		.when('/home', {
			controller:  'HomeCtrl',
			templateUrl: 'app/views/home.html'
		})
		.when('/about', {
			templateUrl: 'app/views/about.html'
		})
		.otherwise({
			redirectTo: '/home'
		});

}]);
```

*app/scripts/controllers/main.js*
``` javascript
angular.module('app.controllers', []);
```

*app/scripts/controllers/HomeCtrl.js*
``` javascript
(function() {

	function HomeCtrl($scope)
	{

	};

	angular
		.module('app.controllers')
		.controller('HomeCtrl', ['$scope', HomeCtrl]);
})();

```

---

### Home view
Here we will put an input with model named search and the ng-change directive with `searchRepositories(search);` value. The `searchRepositories()` method exists in the `HomeCtrl` controller and will fire always the model search change his value.
Next we has a list-group-item with ng-repeat directive, this will loop the `$scope.repositories` variable like a foreach statement and a ng-click directive that will fire the `selectRepository()` method when the user clicks in a list-group-item.

*app/views/home.html*
``` html
<h1>
	Repository Finder
	<small>Search for GitHub repositories.</small>
</h1>
<hr>

<input autofocus type="search" class="form-control" placeholder="Type here to search for repositories"
	ng-model="search" ng-change="searchRepositories(search);">

<hr>

<div class="list-group">
	<a ng-repeat="repository in repositories" ng-click="selectRepository(repository);" class="repository list-group-item">
		<img ng-src="{{ repository.avatar_url }}" class="avatar pull-left img-rounded">
		<b class="h4 text-primary">{{ repository.full_name }}</b>
		<span class="h4 text-success pull-right">{{ repository.language }}</span>
		<br>
		<span class="text-muted">{{ repository.url }}</span>
	</a>
</div>
```

---

### Home controller methods
I prefix with undescore the methods used only in the controller, like the `_init()` method and I only added to `$scope` variable the methods and variables that will be used on the views.

*app/scripts/controllers/HomeCtrl.js*
``` javascript
/* contents omitted for brevity... */
function HomeCtrl($scope)
{
	/* private methods */
	function _init()
	{
		/* init the scope variables */
		$scope.search = '';
		$scope.totalCount = 0;
		$scope.repositories = [];
	};

	/* scope methods */
	$scope.searchRepositories = function(query)
	{
		console.log('query', query);
	};

	$scope.selectRepository = function(repository)
	{
		console.log('repository', repository);
	};

	_init();
};
/* contents omitted for brevity... */
```

---

### App service
Like the controllers, we will create a `main.js` file to create the *app.services* module. And will put a 

*app/scripts/services/main.js*
``` javascript
angular.module('app.services', []);
```
*app/scripts/services/AppService.js*
``` javascript
(function() {

	function App($http)
	{
		return {

			Repository: {

				search: function(query)
				{
					return $http.get('https://api.github.com/search/repositories', {
						params: {
							q: query,
							sort: 'stars',
							order: 'desc'
						}
					});
				}
			}
		};
	};

	angular
		.module('app.services')
		.service('App', ['$http', App]);
})();
```

Instead of put the HTTP requests inside the controller, we will create a service to put all this requests there.
In the `index.html` file include the reference to services file after the controller files, 
and in the `app/scripts/app.js` file include reference to the *app.services* module after the *app.controllers* module. Now, in the `app/scripts/controllers/HomeCtrl.js` file we has to include the App service reference in the controller constructor and the controller params list.

*index.html*
``` html
<!-- content omitted for brevity... -->
<script src="app/scripts/services/main.js"></script>
<script src="app/scripts/services/AppService.js"></script>
<!-- content omitted for brevity... -->
```

*app/scripts/app.js*
``` javascript
angular.module('app', [
	'ngRoute',

	'app.controllers',
	'app.services'
])
/* content ommited for brevity... */
```

*app/scripts/controllers/HomeCtrl.js*
``` javascript
/* ... */
function HomeCtrl($scope, App)
{
	/* content ommited for brevity... */
	$scope.searchRepositories = function(query)
	{
		App.Repository.search(query)
			.success(function(response) {

				$scope.$apply(function() {
					$scope.totalCount = response.total_count;
					$scope.repositories = response.items;
				});

			})
			.error(function(error) {
				console.error(error);
			});
	};
	/* content ommited for brevity... */
};

angular
	.module('app.controllers')
	.controller('HomeCtrl', ['$scope', 'App', HomeCtrl]);
```