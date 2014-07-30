## Angular Expressions, Directives and Filters

We are going to dive into Angular Views. Later we will see how views fit into the Angular architecture. 

## Objectives
* Learn the most common Angular Directives.
* Use Angular Filters in views.
* Show how Angular enables two-way Data Binding with Expressions.
* Validate Forms.
* Introduce the concept of ViewModel, $scope.  

![Angular Overview](AngularComponentOverview1.png)

Just Views for now.

## Demo 

#### Setup

We have a js directory that will contain the Angular javascript, angular.js.


#### First App
Let's create an Angular Single Page Application (SPA).  


* Load Angular js in the page.  
* Set the ng-app directive on the html or body tag.
 	This marks it as a Angular application.   
* Bind data using the ng-model directives and displays data using an angular expression ``{{ }}``

__Create a directives1.html file and add the below. Then open in a browser.__

```
<!doctype html>
 <!-- 1. ng-app -->
 <html ng-app>
  <head>
    <!-- 2. angular javascript -->
    <script type="text/javascript" src='js/angular.js'>
    </script>
  </head>
  <body>
    <h1>First Angular View<h1>
	<!-- 3. ng-model -->
	<input type='text' ng-model='name' placeholder="Enter name"></input>
        <!-- 4. {{ Data Binding Expresssion}} -->
        <p> Name's value is: {{name}}</p>
  </body>
 </html>
```

_Wow, we didn't have to write any javascript. No event handling code!!_

1. The ng-app directive tells the angular.js that this is an angular app.
2. Include the Angular javascript.
3. The ng-model directive is used to create a property in this view's ViewModel, $scope.
4. Data Binding Expression will output the value of the property/attribute.

Each Angular View has a ViewModel that can be accessed via the $scope syntax. It's a container of attributes. We can think that it's just an object literal with properties. 

_We'll see later how $scope fits into the Angular architecture._


#### Directives

_HTML Element attributes or tags provided by Angular that "teaches HTML new tricks"._

Are contained in Views, HTML pages. These are Angular specific HTML Elements attributes and tags that _enhance_ or _extend_ HTML.

* They typically start with __ng-__. But can start with __data-ng-__ to be compatible with HTML validators. 

#### Expressions

Are contained in Views. These are somewhat like a javascript eval in that they can execute javascript. 

The syntax for an expression is ``{{ ... }}`` where ``...`` is any javascript expression.

Some Expressions:  

```
 {{ 3 + 11 }}
  
 {{ "Mr" + name }}
```

#### Data Binding

``{{ name }}`` Data binding syntax.

Previously, we used an control oriented approach to handling changes to elements, controls, on the page. We attached javascript handlers that would process these change _events_. 

With automatic data binding that Angular provides there is no need for all this code. We just _bind_ to the data we're interested in and all places that use that data in the page will change. 

## Lab 1

Add input fields for email and age that have bindings to attributes. Show these attributes using expressions.

## Demo


### ng-hide, ng-click directives.

Lets please HTML validators and use _data-ng-_ directives.

__Create a file directives2.html.__

```
<html data-ng-app>
  <head>
    <script type="text/javascript" src='js/angular.js'> </script>
  </head>
  <!-- initialize name attribute to the value 'James' -->
  <body data-ng-init="name='James'">

    <!-- Bind hide to isHidden -->
    <div data-ng-hide="isHidden">
      <input type='text' data-ng-model="name" placeholder="Enter name"/>
      <p> Name's value is: {{name}}</p>
    </div>

    <!-- Toggle the isHidden property between true and false -->
    Hide: <input type='checkbox' data-ng-model="isHidden"/>
    <br/>
    <!-- Set the name property to Mortimer -->
    <button data-ng-click="name='Mortimer'">Change Name</button>

    <script type='text/javascript' src='js/angular.js'></script>
  </body>
</html>
```

Now we see a couple of new directives. 

* ng-hide - Shows or hides the HTML element depending on the value of the isHidden attribute.  
* ng-init - Evaluates expression, ``name='James'``, in the current scope.  Creates and initializes the name attribute.
* ng-click - Evaluates the expression, `` name='Mortimer` ``. Changes the name attribute's value to 'Mortimer'  

In the Chrome debugger notice how the div surrounding the input field gets the class ng-hide when one clicks the checkbox.



### ng-switch, ng-show directives.


__Create a file directives3.html.__

```
<!doctype html>
<html data-ng-app>
  <head>
    <title>More on Directives</title>
    <link href='css/styles.css' rel="stylesheet" type='text/css'/>
    <script type='text/javascript' src='js/angular.js'></script>
  </head>
  <!-- Set the initial model property, data.    -->
  <body data-ng-init="data={name:'James', isVisible: true, loggedIn: false,   status: 'red'}">
    <div data-ng-switch on="data.loggedIn">
      <div data-ng-switch-when="true">
        Welcome {{data.name}}
      </div>
      <div data-ng-switch-default data-ng-class="data.status">Login</div>
    </div>
    <br/>
    <div data-ng-show="data.isVisible">
      Name: <input type='text' data-ng-model="data.name" />
      {{ data.name }}
    </div>
  </body>
</html>

```


This will create an object literal, data, that is seen in the view. The data.name is shown if you are logged in. Otherwise show a red login.

## Lab 

Change the _"data"__ object literal so that:  
* Input fields are hidden.  
* User is logged in.  


## Documentation

[AngularJS](https://angularjs.org/)

[API Documentation](https://docs.angularjs.org/api)

This is like the $.ajax in JQuery.  
[Ajax HTTP Service](https://docs.angularjs.org/api/ng/service/$http) 