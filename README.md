Tic Tac Toe Reactjs
===================


Using React's TTT Tutorial to learn about Reactjs.

----------


Notes
-------------
- The **slice()** method returns the selected elements in an array, as a new array object. The slice() method selects the elements starting at the given start argument, and ends at, but does not include, the given end argument.

*example:*
```
var fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
    var citrus = fruits.slice(1, 3);
```

*result of citrus:*
```
Orange,Lemon
```
- In the example below slice() method is called to copy the squares array instead of mutating the existing array.
```
  handleClick(i) {
    const squares = this.state.squares.slice();
    squares[i] = 'X';
    this.setState({squares: squares});
  }
```
-	**Functional Components** are a simpler syntax for component types that only consist of a **render** method. Rather than define a class extending **React.Component**, simply write a function that takes props and returns what should be rendered. Take a look at this example:

*before:*
```
class Square extends React.Component {
  render() {
    return (
      <button className="square" onClick={() => this.props.onClick()}>
        {this.props.value}
      </button>
    );
  }
}
```

*after:*
```
function Square(props){
  return (
    <button className="square" onClick={props.onClick}>
      {props.value}
    </button>
  );
}
```
**remember** you'll need to change **this.props** to **props**. Also we also changed ``` onClick={() => props.onClick()} ``` to just ``` onClick={props.onClick} ```, as passing the function down is enough for our example. Note that ``` onClick={props.onClick()} ``` would not work because it would call props.onClick immediately instead of passing it down.

Noteworthy
-------------
-	A **React component class**, or **React component type** takes in paramters, called **props**, and returns a hierarchy of views to display via the **render** method.

-	The **render** method returns a description of what you want to render, and then React takes that description and renders it to the screen. In particular, **render** returns a **React element**, which is a lightweight description of what to render. Most React developers use a special syntax called JSX which makes it easier to write these structures. The ``` <div /> ``` syntax is transformed at build time to ``` React.createElement('div') ```.

example:
```

<div className="shopping-list">
  <h1>Shopping List for {props.name}</h1>
  <ul>
    <li>Instagram</li>
    <li>WhatsApp</li>
    <li>Oculus</li>
  </ul>
</div>

```

is equal to:
```

React.createElement(
  "div",
  { className: "shopping-list" },
  React.createElement(
    "h1",
    null,
    "Shopping List for ",
    props.name
  ),
  React.createElement(
    "ul",
    null,
    React.createElement(
      "li",
      null,
      "Instagram"
    ),
    React.createElement(
      "li",
      null,
      "WhatsApp"
    ),
    React.createElement(
      "li",
      null,
      "Oculus"
    )
  )
);

```
[link](https://babeljs.io/repl/#?presets=react&code_lz=DwEwlgbgBAxgNgQwM5IHIILYFMC8AiJACwHsAHUsAOwHMBaOMJAFzwD4AoKKYQgRlYDKJclWpQAMoyZQAZsQBOUAN6l5ZJADpKmLAF9gAej4cuwAK5wTXbg1YBJSswTV5mQ7c7XgtgOqEETEgAguTuYFamtgDyMBZmSGFWhhYchuAQrEA) to working example.

- You can put any JavaScript expression within braces inside JSX. Each React element is a real JavaScript object that you can store in a variable or pass around your program.

- Whenever ``` this.setState ``` is called, an update to the component is scheduled, causing React to merge in the passed state update and rerender the component along with its descendants.

example:
```
 constructor(props) {
   super(props);
   this.state = {
     value: null,
   };
 }

render() {
    return (
      <button className="square" onClick={() => this.setState({value: 'X'})}>
        {this.state.value}
      </button>
    );
  }

```
- In the example above, when the component rerenders, ``` this.state.value ``` will be ``` 'X' ``` so you'll see an X in the grid. If you click on any square, an X should show up in it.

- When you want to aggregate data from multiple children or to have two child components communicate with each other, move the state upwards so that it lives in the parent component. The parent can then pass the state back down to the children via props, so that the child components are always in sync with each other and with the parent.

- Pulling state upwards like this is common when refactoring React components.

- The **onClick** prop on the build-in DOM **<button>** component tells React to set up a click event listener.

- When a component no longer keeps its own state; it receives its value from its parent component and informs its parent when its clicked. We call components like this **controlled components**.




es6
-------------
- The JavaScript **arrow function** syntax. When passing a function as the **onClick** prop to a button tag we need to do something like this:
```
onClick={() => alert('click')}>

```
because doing:
```
onClick={alert('click')}

```
would alert immediately instead of when the button is clicked.
