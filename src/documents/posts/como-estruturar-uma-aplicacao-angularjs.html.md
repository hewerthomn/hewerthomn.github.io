```
title: Como estruturar um app AngularJS
layout: post
tags: ['angular']
date: 2014-12-05
```
Olá!

Após finalizar o [tutorial PhoneCat](https://docs.angularjs.org/tutorial) na página de documentação oficial do AngularJS, comecei a pensar como eu poderia estruturar melhor um app com AngularJS.

O app criado no tutorial é bem simples e os módulos são incluídos em um único arquivo javacript como no arquivo `controllers.js`.
Usar essa estrutura não será um problema se seu app for bem pequeno, como o do tutorial, mas se ele começar a crescer com o tempo, essa abordagem será mais complicada de manter.

Então fui atrás de pesquisar como eu poderia estruturar melhor o app e aplicar algumas boas práticas de nomenclatura de módulos.

Vamos começar! :D

*Isso não é um guia definitivo e não tem pretensão de ser, apenas foi uma forma que encontrei para melhor organizar os códigos.*

---

#### Configurar dependências

Primeiro precisamos configurar algumas dependências para iniciar o desenvolvimento.
Se você já tem o *nodejs*, *npm* e o *bower* instalados, avance para o próximo tópico.

A primeira dependência a instalar é o [nodejs](http://nodejs.org/) (e o npm se não estiver instalado).

Depois do npm instalado, precisamos instalar o [bower](http://bower.io/) para gerenciar os pacotes font-end.

```
$ npm install -g bower
```
O parâmetro -g instala o pacote bower globalmente para poder executar de qualquer diretório.

Para testar se o bower está funcionando corretamente, execute o comando `bower` no terminal para ver a lista de comandos disponíveis.

--- 

#### Estutura de diretórios

Crie o diretório do projeto e navegue até ele.

```
$ mkdir myapp && cd myapp
```

A estrutura básica de diretórios pode ser como abaixo.

Você deve adicionar outros diretórios se precisar deles, como por exemplo `app/tests`, `app/scripts/providers`, etc.

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

Para criar todos esses diretórios de uma vez execute o comando abaixo no terminal:

```
mkdir -p app/scripts/controllers && mkdir app/scripts/directives && mkdir app/scripts/services && mkdir -p app/views/directives && mkdir app/views/partials && mkdir css && mkdir img
```

--- 

#### Instalando os pacotes

Eu prefiro mudar o diretório padrão dos pacotes do bower chamado `bower_components` para `packages`, para fazer isso crio um arquivo `.bowerrc` no diretório raiz do projeto com o seguinte conteúdo:

``` javascript
{
  "directory": "packages"
}
```

Agora vamos instalar o AngularJS executando o comando abaixo no terminal:
```
bower install angular angular-route
```

Esse simples comando irá clonar o repositório do AngularJS e do pacote angular-route no diretório de pacotes.

---

#### Criar a página index

Adicionei o tema [Yeti do Bootstrap](https://bootswatch.com/yeti/) para a interface mais agradável e um arquivo css para os estilos do app.
A diretiva `ng-view` é o local onde será exibido o conteúdo renderizado das views. Mais abaixo é incluído os arquivos de scripts das bibliotecas utilizadas e os do app.

*Se você usou o diretório padrão do bower, o caminho das bibliotecas começará com `bower_componenets`.*

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

O arquivo `app/scripts/app.js` é onde nós configuramos o app. Aqui definimos os módulos usados e as configurações globais, como as rotas. O arquivo `app/scripts/controllers/main.js` é apenas para criar o módulo vazio *app.controllers*.

Em seguida, o arquivo `app/scripts/controllers/HomeCtrl.js` tem um controller vazio dentro de uma função anônima auto-invocada ([IIFE](http://en.wikipedia.org/wiki/Immediately-invoked_function_expression)).

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

#### View home

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