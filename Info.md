# REDUX NOTE

From [ https://learn.freecodecamp.org/front-end-libraries/redux ] freeCode

- Single State Object
- Is housed in the Redux Store (Update store must do so through the Redux store )
- createStore() : requires reducer method
- Redux Methods are available from a Redux Object and provides several methods
***
### Create Store

` const reducer = (state = 5) => {
  return state;
} `

` // Redux methods are available from a Redux object`

` // For example: Redux.createStore()`

` // Define the store here:`

` const store = Redux.createStore(reducer);`
### Methods
***
- getState() _retrieve_(recupera) the current state. **example**; store.getState()

`
const store = Redux.createStore(
  (state = 5) => state
);
`
#### apply other method
***
`// change code below this line`

`const currentState = store.getState();`

### Actions
***
- State Update is triggered by dispatching actions
- Action is a simply js object. Sometimes also carries some data is optional.  Must carry TYPE property.
- Like messengers, Redux actions inform about the app events to the Redux Store.

`// Define an action here:`

`const action = {type: 'LOGIN'};`
### Actions Creators
***
- Action creators sending action to the store. Is a simple js Function and returns an action. Is as the calling the action.

` const action = {
  type: 'LOGIN'
} `

`// Define an action creator here:`

`function actionCreator(){
    return action;
} `
