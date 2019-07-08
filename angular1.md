# Angular

```javascript
var app = angular.module("myApp", []);
```

```html
<body ng-app="myApp">
```
```javascript
app.controller('MainController', ['$scope', function($scope) { 
  $scope.title = 'Top Sellers in Books'; 
}]);
```
```html
<div class="main" ng-controller="MainController">
  <h1>{{ title }}</h1>
  ```
Awesome! You built an AngularJS app. How does it work?  

In app.js, we created a new module named myApp. A module contains the different components of an AngularJS app.  

Then, in index.html we added `<body ng-app="myApp">`. The ng-app is called a directive. It tells AngularJS that the myApp module will live within the <body> element, termed the application's scope. In other words, we used the ng-app directive to define the application scope.  

In MainController.js we created a new controller named MainController. A controller manages the app's data. Here we use the property title to store a string, and attach it to `$scope`.  

Then, in index.html, we added `<div class="main" ng-controller="MainController">`. Like ng-app, ng-controller is a directive that defines the controller scope. This means that properties attached to $scope in MainController become available to use within `<div class="main">`.  

Inside `<div class="main">` we accessed $scope.title using `{{ title }}`. This is called an expression. Expressions are used to display values on the page.  

The value of title showed up when we viewed the app in the browser.  
