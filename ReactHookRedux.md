# React hooks:
- Replacement for existing lifecycle methods for pure functional components
- Additional feature is watching changes in the existing properties using `useEffect` or `useLayoutEffect` and performing some extra functionality on change. But it is also limited to the component it self.
- The same goes for the memoization hooks like `useCallback` and `useMemo`.
- Would need to use context API for transferring data down deep heirarchy and using in other components

## Pros:
- State management and optimization using memoization technique is good within the component
- Code looks cleaner and more readable than in class based components by using hooks
- Ability to observe changes in the component's variables.

## Cons:
- Context API creates unnecessary coupling within the component.
- As the number of components increase and the communication between them increases, the maintainance and readability of the code also becomes poor.
- Also rendering cycle becomes huge problem, as any change related (expected) and unrelated (unexpected) would also lead to render cycle being triggered.
- If we avoid context API then there would be lots of props being passed from one component to other, which would make the code highly unreadable and difficult to maintainance
- The other way to deal is by using global states, but again it would need good design for it as it also may lead to unnecessary render cycles.

# Redux:
- Redux is a predictable state management library
- Have a single source of truth, because of that it is possible to transfer the value of state changed in component becomes much easier.

## Pros
- Determinstic state resolution and view renders
- Transactional state
- Total seperation of data, sideEffects and presentation layer
- Single source of truth
- Easy to share data between components (without context related dependency)
- Automatically log telemetry and connects it with time-travel debugger
- Store design before components can make it easier to understand high level design of the components.

## Cons
- Extra learning curve
- Should be intelligent on how to use Redux
- Don't place every change inside the Redux store.

# Conclusion:
React hooks are not replacement for redux. They are simply a replacement for the lifecycle methods present in the class methods. Using Redux with React encourages separation of concerns by keeping data and presentation layer separate. Debugging of state change also becomes very easy. With introduction, react hooks, react hooks can be and whereever possible should be used in parallel with

For instance, there is a functional component which holds an input field, and the change from it needs to be only propagated when the input is valid and an Enter is clicked inside the field. In that case, the right design would be to use the `useState` hook of react for maintainting a state which can be used for validating and triggering a `dispatch` to update the `state` of redux would be easy to understand and maintain. And reduces unnecessary change in store's state.
