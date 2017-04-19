# React Cheatsheet

### Hello World
```jsx
var element = <h1>Hello World</h1>;
ReactDOM.render(element, document.body);

```
### Components

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
class ComponentES6 extends Component{
  render() {
    return <div>Hello Peter</div>;
  }
}

ReactDOM.render(<ComponentES6 />, document.body);
``` 


### Component + Props

#### ES5
```jsx
var Component = React.createClass({
  render: function () {
    return <div>Hello {this.props.name}</div>;
  }
});

ReactDOM.render(<Component name="Peter" />, document.body);

```

#### ES6

```jsx
class ComponentES6 extends Component{
  render() {
    return <div>Hello {this.props.name}</div>;
  }
}

ReactDOM.render(<ComponentES6 name="Peter" />, document.body);
``` 



### Nesting Components

#### ES5

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

#### ES6

```jsx
class User extends Component {...}
class Text extends Component {...};

class Info extends Component{
  render() {
    return <div>
      <User />
      <Text />
    </div>;
  }
}

```
### Events

#### ES5

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

#### ES6

```jsx
class Button extends Component{
	//...
	handleClick(e){
		// e is ein SyntheticEvent (cross-browser-kompatibel)
		alert('Hello!');
	},
	render(){
		// Mit dem Attribut onClick die Funktion übergeben
		return <button onClick={this.handleClick}>Say hello.</button>;
	}
}

```

### State

#### ES5

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

#### ES6


```jsx
class MyButton extends Component{

  // Initialzustand im Constructor setzen
  constructor(){
    super();
    this.state = {
    	name: 'Peter'
    }
  },
      
  myFunc(){
     // State aktualisieren
     this.setState({ name:'Jon' });
  },
			
  render(){
    // Auf State greift man über this.state zu
    return <button>{this.state.name}</button>;
  }
}

```
### Lists

```jsx
// Im Konstruktor ein Array als State anlegen
  constructor() {
    super();
    this.state = {
      todos: [
        {id: "1", text: "To Do 1"},
        {id: "2", text: "To Do 2"}
      ]
    }
  }
  
  
// Mit der Map-Funktion das Array als Liste ausgeben und eindeutige keys definieren
  render() {
    return (
        <ul>
        {this.state.todos.map(item => (
            <li key={item.id}>{item.text}</li>
        ))}
        </ul>
    );
  }
```

### Lifecycle

```jsx
class Clock extends React.Component{

  constructor(props){
  	super(props);
	this.state = {
    		time : new Date()
    	}
  }
  
  componentDidMount(){
  	this.timer = setInterval(() => this.tick(), 1000);
  }
  
  componentWillUnmount(){
  	clearInterval(this.timer);
  }
  
  tick(){
  	this.setState({time : new Date()});
  }
	
  render(){
  	return <h2>{this.state.time.toLocaleTimeString()}</h2>
  }
}
```

### Forms

```jsx

class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

### fetch()

https://facebook.github.io/react-native/docs/network.html

#### GET

```javascript

fetch("http://todo.jecode.de/todos")
  .then(response => response.json())
  .then(json => {
    alert(json);
   });
```

#### POST

```javascript

fetch('https://mywebsite.com/endpoint/', {
  method: 'POST',
  body: JSON.stringify({
    firstParam: 'yourValue',
    secondParam: 'yourOtherValue',
  })
})
```
