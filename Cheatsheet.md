# React Cheatsheet

### Component
```javascript
var Component = React.createClass({
  render: function () {
    return <div>Hello Peter</div>;
  }
});

ReactDOM.render(<Component />, document.body);

```

### Component + Props
```javascript
var Component = React.createClass({
  render: function () {
    return <div>Hello {this.props.name}</div>;
  }
});

ReactDOM.render(<Component name="Peter" />, document.body);

```


### State
```javascript
var MyButton = React.createClass({
			
      getInitialState: function(){
      	return {
        	name: 'Peter'
        };
      },
      
      myFunc: function(){
	// State setzen
	this.setState({ name:'Jon' });
      },
			
      render: function(){
      	return <button>{this.state.name}</button>;
      }
});

```
