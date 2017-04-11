# React Cheatsheet

### Component
```jsx
var Component = React.createClass({
  render: function () {
    return <div>Hello Peter</div>;
  }
});

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
