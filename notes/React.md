How to create a component with a child component: 

```javascript
class App extends React.Component{
    constructor(){
        super();
        this.state ={
            txt: "this is the state test"
        }
    }
    update ( e ){
        this.setState({txt: e.target.value})
    }
    render(){
        return (
        <div> 
       	<h1>{this.state.txt}</h1>
        <widget update={this.update.bind{this}} />    
        </div>
        )
    }
}

const Widget = (props) =>
	<input type = "text" 
		   onChange={props.update}></input>
```

How to create Nested Data with React props.children

```javascript
class App extends React.Component{
    render(){
        return <button> I <Heart /> React </button>
    }
}

//const Button = (props) =><button>{props.children}</button>

class Heart extends React.Component{
    render(){
        return <span>&hearts;</span>
    }
}
```

