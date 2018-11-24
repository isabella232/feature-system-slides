## Scaling React in big codebases using features

Big-scale projects often require rewriting the same logic (Redux actions, reducers, sagas, etc.) whenever UI components are reused in different parts of the system as these concerns are traditionally implemented in а specific rather than generic way.

The Feature System we use at TwentyThree offers a great way to reuse business logic through component composition and reduce boilerplate code. We achieve this by bundling together a UI component and its logic into a composite component, which takes a namespace property to store associated data in an isolated scope of the state tree. This makes scaling big projects fast and easy.

The core concept allows implementing actions, reducers, sagas and selectors in a generic way, storing state of each component instance independently to avoid collisions and binding business logic on demand whenever the composite component is mounted.

A good example is a list component. Typically building such a component requires handling different states of the list such as an empty state and a loading state, fetching data, infinite scrolling, etc. You would want to share all this business logic whenever a list component is reused, but the state and all actions should be unique to each instance to avoid multiple lists on the same page to react to the same events and state changes. A ListFeature component can be seen as a composite component that takes a namespace and an endpoint from which to fetch data. The business logic is written once and can be reused by every ListFeature instance.

The Feature System also helps to reduce boilerplate code by providing primitives to generate Redux actions and make them available in reducers and components.

In summary, the Feature System facilitates writing reusable business logic, DRY code where changes can be implemented centralistically and saves development time when reusing complex components.
