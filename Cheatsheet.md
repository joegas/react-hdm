# React Cheatsheet

### Hello World
```jsx
var element = <h1>Hello World</h1>;
ReactDOM.render(element, document.body);

```
### Component

#### ES5

```jsx
var Component = React.createClass({
  render: function () {
    return <div>Hello Peter</div>;
  }
});

ReactDOM.render(<Component />, document.body);

```

#### ES6
```jsx
class Component extends Component{
  render() {
    return <div>Hello Peter</div>;
  }
};

ReactDOM.render(<Component />, document.body);
``` 


### Component + Props
```jsx
var Component = React.createClass({
  render: function () {
    return <div>Hello {this.props.name}</div>;
  }
});

ReactDOM.render(<Component name="Peter" />, document.body);

```


### Nesting Components
```jsx
var User = React.createClass({...});
var Text = React.createClass({...});

var Info = React.createClass({
  render() {
    return <div>
      <User />
      <Text />
    </div>;
  }
});

```

### Events
```jsx
var Button = React.createClass({
	
	handleClick: function(e){
		// e is ein SyntheticEvent (cross-browser-kompatibel)
		alert('Hello!');
	},
	render: function(){
		// Mit dem Attribut onClick die Funktion übergeben
		return <button onClick={this.handleClick}>Say hello.</button>;
	}
});

```

### State
```jsx
var MyButton = React.createClass({

  // Initialzustand setzen
  getInitialState: function(){
    return {
      name: 'Peter'
    };
  },
      
  myFunc: function(){
     // State aktualisieren
     this.setState({ name:'Jon' });
  },
			
  render: function(){
    // Auf State greift man über this.state zu
    return <button>{this.state.name}</button>;
  }
});

```
