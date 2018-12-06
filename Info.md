# REDUX NOTE

From [ https://learn.freecodecamp.org/front-end-libraries/redux ] freeCode

- Single State Object
- Is housed in the Redux Store (Update store must do so through the Redux store )
- createStore() : requires reducer method
- Redux Methods are available from a Redux Object and provides several methods
***
### Create Store

    const reducer = (state = 5) => {
      return state;
    }
    // Redux methods are available from a Redux object
    // For example: Redux.createStore()
    // Define the store here:
    const store = Redux.createStore(reducer);
***
### Methods

- getState() _retrieve_(recupera) the current state. **example**; store.getState()

      const store = Redux.createStore(
        (state = 5) => state
      );
      // change code below this line
      const currentState = store.getState();
***
### Actions
- State Update is triggered by dispatching actions
- Action is a simply js object. Sometimes also carries some data is optional.  Must carry TYPE property.
- Like messengers, Redux actions inform about the app events to the Redux Store.

      // Define an action here:
      const action = {type: 'LOGIN'};
***
### Actions Creators
- Action creators sending action to the store. Is a simple js Function and returns an action. Is as the calling the action.

      const action = {
        type: 'LOGIN'
      }

      // Define an action creator here:

      function actionCreator(){
          return action;
      }
***
### Redux: Dispatch an Action Event
- DISPATCH: dispatch the action to Redux Store. Recall action creators and object with a type property. Then the method dispatches an action object to the Redux store.

      const store = Redux.createStore(
        (state = {login: false}) => state
      );

      const loginAction = () => {
        return {
          type: 'LOGIN',
          state: {login: true}
        }
      };

      // Dispatch the action here the approach is you can add a logic here and return the object that you need:
      store.dispatch(loginAction);
      //The same is for the next code
      store.dispatch({type: 'LOGIN'})
      
***
### REDUCER
**Handle an Action in the Store**
- REDUCER (Handle an Action in the Store):  Responsible State modification in response to actions. Takes a STATE and ACTION as arguments and always return a new State. is the only role to the reducer. The state is Read-Only, so Reducer must always return a new copy of state and never modify state directly.

      const defaultState = {
        login: false
      };

      const reducer = (state = defaultState, action) => {
       // change code below this line
        if(action.type === 'LOGIN'){
          return {login: true}
          }else{
            return state;
          }

      // change code above this line
      };

      const store = Redux.createStore(reducer);

      const loginAction = () => {
        return {
          type: 'LOGIN'
        }
      };
***
### SWITCH STATEMENT
** Handle multiple actions
- Use a SWITCH Statement to Handle Multiple Actions. You can tell the Redux store how to handle multiple action types.

      // change code below this line
      // change code above this line

      const defaultState = {
        authenticated: false
      };

      const authReducer = (state = defaultState, action) => {
      switch (action.type) {
      case 'LOGIN':    
      return {    
      authenticated: true
      }

      case 'LOGOUT':
      return {
      authenticated: false
      }

       default:   
      return state;
      }

      };

      const store = Redux.createStore(authReducer);

      const loginUser = () => {
      return {  
       type: "LOGIN"
      } 
      };
      const logoutUser = () => {
        return {
        type: "LOGOUT"
        }
      };
***
### SUBSCRIBE
** Register a Store Listener. **
- "store.subscribe()" is a REDUX method that subscribe listener function to the store, are called whenever an action is despatched against the store. Simply logs a message every time an action is received and the store is updated.

      const ADD = 'ADD';

      const reducer = (state = 0, action) => {
       switch (action.type) {
          case ADD:
            return state + 1;    
          default:
          return state;
        }
      };

      const store = Redux.createStore(reducer);
      // global count variable:
      let count = 0;
      // change code below this line
      const callback = () => {
        count++;
      }

      store.subscribe(callback);
      // change code above this line
      store.dispatch({ type: ADD });
      console.log(count);
      store.dispatch({ type: ADD });
      console.log(count);
      store.dispatch({ type: ADD });
      console.log(count);
***
### COMBINE MULTIPLE REDUCERS:
- Divide State into multiple pieces with multiple reducers if the app grows. Need a root to pass all reducers into createStore(). In order to let us combine multiple reducers together, Redux provides the combineReducers() method.

      const INCREMENT = 'INCREMENT';
      const DECREMENT = 'DECREMENT';

      const counterReducer = (state = 0, action) => {
        switch(action.type) {
          case INCREMENT:
            return state + 1;
          case DECREMENT:
            return state - 1;
          default:
            return state;
        }
      };

      const LOGIN = 'LOGIN';
      const LOGOUT = 'LOGOUT';

      const authReducer = (state = {authenticated: false}, action) => {
        switch(action.type) {
          case LOGIN:
            return {
              authenticated: true
            }
          case LOGOUT:
            return {
              authenticated: false
            }
          default:
            return state;
        }
      };

      // define the root reducer here

      const rootReducer = Redux.combineReducers({
        count: counterReducer,
        auth: authReducer
      })

      const store = Redux.createStore(rootReducer);
***
### SEND ACTION DATA TO THE STORE
- Action can send other information than a type. Is common that action send extra data by user interactions.

      const ADD_NOTE = 'ADD_NOTE';

      const notesReducer = (state = 'Initial State', action) => {
        switch(action.type) {
          // change code below this line
          case ADD_NOTE:
          return state = action.text;
          break;
          // change code above this line
          default:
            return state;
        }
      };

      const addNoteText = (note) => {
        // change code below this line
        return {
          type: ADD_NOTE,
          text: note
        }
        // change code above this line
      };

      const store = Redux.createStore(notesReducer);

      console.log(store.getState());
      store.dispatch(addNoteText('Hello!'));
      console.log(store.getState());
***


***
***
Notes: 
* Error: Unexpected character '​' ... Fixed with copie paste all the code from zero;
* Error: Does not finded a redux module, fixed with npm install --save redux
* When I created a new switch statement don't returned in default the current state and send me a error message with the default word because the function return default.
