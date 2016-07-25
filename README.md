[logo]: https://www.wagonhq.com/images/posts/react.png "React Logo"
![alt text][logo]
#React Resources and information

##JavaScript

#####Array.map

In Javascript ([source](http://www.w3schools.com/jsref/jsref_map.asp)):

_Definition and Usage_

The map() method creates a new array with the results of calling a function for every array element.

The map() method calls the provided function once for each element in an array, in order.

_Note: map() does not execute the function for array elements without values._

_Note: map() does not change the original array._

Example:

```javascript
var numbers = [4, 9, 16, 25];

function myFunction() {
    x = document.getElementById("demo")
    x.innerHTML = numbers.map(Math.sqrt);
}
```

Returns:

```javascript
2,3,4,5
```

Syntax:

```javascript
array.map(function(currentValue,index,arr), thisValue)
```

Additional Examples:

```javascript
var numbers = [65, 44, 12, 4];

function multiplyArrayElement(num) {
    return num * document.getElementById("multiplyWith").value;
}

function myFunction() {
    document.getElementById("demo").innerHTML = numbers.map(multiplyArrayElement);
}
```

```javascript
var persons = [
    {firstname : "Malcom", lastname: "Reynolds"},
    {firstname : "Kaylee", lastname: "Frye"},
    {firstname : "Jayne", lastname: "Cobb"}
];


function getFullName(item,index) {
    var fullname = [item.firstname,item.lastname].join(" ");
    return fullname;
}

function myFunction() {
    document.getElementById("demo").innerHTML = persons.map(getFullName);
}
```

Applied in React ([source](https://thinkster.io/iterating-and-rendering-loops-in-react)):

_Framing the problem_

Iterating and displaying data is a very common part of building applications. In React (and other frameworks), the most basic way of doing this is hard coding the entries into your HTML ([view code](http://jsfiddle.net/danielvassallo87/jy7r30ov/)):

```javascript
var Hello = React.createClass({
    render: function() {
        return (
            <ul>
                <li>Jake</li>
                <li>Jon</li>
                <li>Thruster</li>
            </ul>
        )
    }
});
```

Easy enough! But what if our names were in an array, and couldn’t be hard coded into the component? In other words, how could we iterate over `[‘Jake’, ‘Jon’, ‘Thruster’]` and create LI’s for each of them?

_Vanilla Javascript to the rescue_

One of the best things about React is that doesn’t require you to learn a myriad of new methods to manipulate & render data. Instead, it relies heavily on the Javascript language itself for these common tasks. Remember that [React will evaluate any Javascript expression you provide it](https://facebook.github.io/react/docs/jsx-in-depth.html#javascript-expressions), and this also includes arrays (it renders each array entry, starting at index 0). For those of you who are Javascript experts, you’ll know that we can use Javascript’s [`map` method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) to quickly iterate over our array and create a new one with our desired values!

Not so fast though — also remember that `<li>Jake</li>` actually boils down to `React.createElement('li', null, ‘Jake’)`, so our elements are actually just methods that will be executed. What this means is that we need to convert our array from `[‘Jake’, ‘Jon’, ‘Thruster’]` to

```javascript
[React.createElement('li', null, ‘Jake’), React.createElement('li', null, ‘Jon’), React.createElement('li', null, ’Thruster’)]
```

— and since we’re using JSX (thank you programming gods), it would instead look super pretty:

`[<li>Jake</li>, <li>Jon</li>, <li>Thruster</li>]`.

Put that all together and you get:

```javascript
var Hello = React.createClass({
    render: function() {
        var names = ['Jake', 'Jon', 'Thruster'];
        return (
            <ul>
                {names.map(function(name, index){
                    return <li key={ index }>{name}</li>;
                  })}
            </ul>
        )
    }
});
```

_Note that we're using the 'key' attribute to ensure our elements are uniquely [identified](https://facebook.github.io/react/docs/multiple-components.html#dynamic-children)._

Our component is now programmatically listing out Jake, Jon and Thruster! You can check out the working code [here](http://jsfiddle.net/danielvassallo87/mdhkszd8/)!

Best Practices

The last thing we’ll do is tidy our code up a bit. As your components grow in size you’ll want to abstract as much code out of the return statement as possible. This typically requires setting your desired output in variables. It’s quite simple to do this:

```javascript
var Hello = React.createClass({
    render: function() {
        var names = ['Jake', 'Jon', 'Thruster'];
        var namesList = names.map(function(name){
                        return <li>{name}</li>;
                      })

        return  <ul>{ namesList }</ul>
    }
});
```

You can check out the working code [here](http://jsfiddle.net/danielvassallo87/07r6wa9w/)!

#####Array.reduce
#####Pure Functions
#####.bind
#####this

##React
#####Imperative vs Declarative
#####Composition
#####Unidirectional Dataflow
#####JSX
#####Virtual DOM
#####createClass
#####state
#####props
#####props.children
#####createElement
#####Lifecycle Hooks
#####Container vs Presentational Components
#####Stateless Functional Components
#####Events
#####Private Stateless Functional Components

##React Router
#####Declarative Routing
#####Route Configurations
#####Route Matching
#####Animating Route Transitions
#####Query Parameters
##Webpack
#####Configuration
#####HTMLWebpackPluginConfig
#####CSS Loader

##NPM
