**##REDUX NOTES**

From https://learn.freecodecamp.org/front-end-libraries/redux

- Single State Object
- Is housed in the Redux Store (Update store must do so through the Redux store )
- createStore() : requires reducer method
- Redux Methods are available from a Redux Object and provides several methods

##Create STore
const reducer = (state = 5) => {
  return state;
}

// Redux methods are available from a Redux object
// For example: Redux.createStore()
// Define the store here:

const store = Redux.createStore(reducer);

-  getState() retrieve (recupera) the current state example - store.getState() - ;

const store = Redux.createStore(
  (state = 5) => state
);

// change code below this line
const currentState = store.getState();
