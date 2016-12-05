# react-global-state

Sometimes you want global state in React, but you don't want the added complexity of using Redux. What if calling `setState` could update your entire state tree?

## Installation

`npm install --save react-global-state`

or

`yarn add react-global-state`

## Usage

Wrap your components with `gs`. Your global state will be available as the `state` and `setState` props.

	import {gs} from 'react-global-state';
	
	class Button extends Component {
        onClick() {
            const {state, setState} = this.props;
            setState({counter: (state.counter) ? state.counter+1 : 1});
        }
    
        render() {
            const {state} = this.props;
            return <div onClick={this.onClick.bind(this)}>Click me</div>
        }
    }
    
    class Display extends Component {
        render() {
            const {state} = this.props;
            return <div>Counter value: {state.counter}</div>
        }
    }
    
    const WrappedButton = gs(Button);
    const WrappedDisplay = gs(Display);
    
    class App extends Component {
        render() {
            const {state} = this.props;
            return (
            <div className="App">
                <WrappedButton />
                <WrappedDisplay />
            </div>
            );
        }
    }

## Inspired by...

Redux, which I love and which you should use if your app has the least bit of complexity.





