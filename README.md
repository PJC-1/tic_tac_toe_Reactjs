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
