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
***
### Methods

- getState() _retrieve_(recupera) the current state. **example**; store.getState()

`
const store = Redux.createStore(
  (state = 5) => state
);
`

`// change code below this line`

`const currentState = store.getState();`
***
### Actions
- State Update is triggered by dispatching actions
- Action is a simply js object. Sometimes also carries some data is optional.  Must carry TYPE property.
- Like messengers, Redux actions inform about the app events to the Redux Store.

`// Define an action here:`

`const action = {type: 'LOGIN'};`
***
### Actions Creators
- Action creators sending action to the store. Is a simple js Function and returns an action. Is as the calling the action.

` const action = {
  type: 'LOGIN'
} `

`// Define an action creator here:`

`function actionCreator(){
    return action;
} `
***
### Redux: Dispatch an Action Event

`const store = Redux.createStore(
  (state = {login: false}) => state
);`

`const loginAction = () => {
  return {
    type: 'LOGIN',
    state: {login: true}
  }
};`

`// Dispatch the action here the approach is you can add a logic here and return the object that you need:`

`store.dispatch(loginAction);`

`//The same is for the next code`

`store.dispatch({type: 'LOGIN'})`
***
### REDUCER
**Handle an Action in the Store**
- REDUCER (Handle an Action in the Store):  Responsible State modification in response to actions. Takes a STATE and ACTION as arguments and always return a new State. is the only role to the reducer. The state is Read-Only, so Reducer must always return a new copy of state and never modify state directly.


`const defaultState = {
  login: false
};`

`const reducer = (state = defaultState, action) => {`

 ` // change code below this line`

`if(action.type === 'LOGIN'){
  return {login: true}
  }else{
    return state;
  }`

`// change code above this line`

`};`

`const store = Redux.createStore(reducer);`

`const loginAction = () => {
  return {
    type: 'LOGIN'
  }
};`






Note: 
