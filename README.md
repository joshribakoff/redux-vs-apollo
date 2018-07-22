# redux-vs-apollo

This repo is to capture my WIP thoughts on the question of "redux vs apollo client". Most of this wont make sense to anyone until I clean up my notes.

- redux reduces state from actions (operations), apollo updates state with mutations (operations)
  - research on CRDTs show one can emulate the other
    - 1x only delivery, who will acknowledge the acknowledgement
    - model actions in graphql, use uuid to de-duplicate
    - redux actions can cause a reducer to either update state or append to state
- redux separates asynchronous logic & state changes, separation of concerns
  - PRO - library not framework approach allows using different middleware at appropriate level of abstraction
- apollo does not offer pedictable guarentees to order mutations are executed
- apollo allows mixing these concerns in `update()` functions
- redux doesnt dictate how to model state. apollo requires usage of graphql
- redux doesnt preclude from using graphql
- redux allows accidently working at the wrong level of abstraction [too low]
- apollo allows accidently working at the wrong level of abstraction [too high]
- redux is reactive, because it encourages a single source of truth, all computed state is calculated client side / selectors react
- apollo is proactive, for "computated state" that is managed server side, you have to tell it what queries to refetch and/or explicitly update the state imperatively
- Both can be considered "global state" ... you pass apollo client / redux store down the component tree via the context API.  Contrast this with the original flux pattern with multiple stores where the stores could hold duplicate data that got out of sync
- apollo / nor redux fully solve the issue... see above point about it being sometimes unreasonable to dowload and calculate derived data client side. at some point your app scales and you need to move things to the server and introduce a new field (duplicating data)

TODO - implement distributed counter using both paradims, showing pitfalls and how to overcome

TODO - talk about testability

TODO - talk about performance

TODO - talk about single source of truth, computed state/memoized selectors. tradeoffs with server computing state. if i fetch an aggregate value summarizing my data for Page A and the raw data being aggregated is shown on Page B, those values can get out of sync in the store. if I fetch my entire data store into redux just to aggregate data client side that has direct tradeoffs with some of the issues graphql intends to solve. 

TODO - talk about the question should redux actions model user's intent vs leaking implementation details (actions named addToTodosById)

 > I guess I think this is an inexcusable thing to do, since 90% of redux value is in the ecosystem. Any kid can reimplement the Redux pattern, so that’s not important. The important thing is compatibility with the vast range of available packages and patterns.
 - Shasko Stubailo
 - https://forums.meteor.com/t/reactive-programming-rxjs-5-observable-and-redux-store-saga-in-angular2-meteor/25662/6
 - Why did Apollo drop redux support and implement their own cache, etc...
