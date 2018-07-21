# redux-vs-apollo

This repo is to capture my WIP thoughts on the question of "redux vs apollo client". Most of this wont make sense to anyone until I clean up my notes.

- redux reduces from state from actions (operations), apollo updates state
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

TODO - implement distributed counter using both paradims, showing pitfalls and how to overcome
TODO - talk about testability
TODO - talk about performance
