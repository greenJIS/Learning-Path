# React — Learning Curve (based on react.dev)

Goal: Follow a progressive plan that maps to the official React docs at react.dev.

# Learn – React Documentation

## Get Started

- **[Quick Start](https://react.dev/learn)**
  High-level introduction to React: components, JSX, props, state, and rendering. Don't need to learn aything, just stick with it and try to understad the English sentences.
- **[Tutorial: Tic-Tac-Toe](https://react.dev/learn/tutorial)**
  Step-by-step walkthrough building a small game while learning key concepts. It's fun if you have some idea of react, if not then temporarily skip after overview.
- **[Thinking in React](https://react.dev/learn/thinking-in-react)**
  Essential module to read. It describes how to break UI into components, define data flow, and design React apps. It is also reading and get the idea.

## Learn React

### Describing the UI

- **[Describing the UI](https://react.dev/learn/describing-the-ui)** (Overview)
  Core philosophy: components describe UI based on data.
- **[Your First Component](https://react.dev/learn/your-first-component)**  
  How to define and render your first functional component.
- **[Importing and Exporting Components](https://react.dev/learn/importing-and-exporting-components)**  
  Organizing components across multiple files.
- **[Writing Markup with JSX](https://react.dev/learn/writing-markup-with-jsx)**  
  JSX syntax, rules, and why React uses JSX.
- **[JavaScript in JSX with Curly Braces](https://react.dev/learn/jsx-curly-braces)**  
  How to embed dynamic values and expressions inside JSX.
- **[Passing Props to a Component](https://react.dev/learn/passing-props-to-a-component)**  
  How parent components send data to child components.
- **[Conditional Rendering](https://react.dev/learn/conditional-rendering)**  
  Rendering different UI states based on logical conditions.
- **[Rendering Lists](https://react.dev/learn/rendering-lists)**  
  How to loop over arrays and the correct usage of keys.
- **[Keeping Components Pure](https://react.dev/learn/keeping-components-pure)**  
  Why components must remain pure for predictable rendering.
- **[Your UI as a Tree](https://react.dev/learn/your-ui-as-a-tree)**  
  Understanding component hierarchies and React’s virtual DOM tree.

---

### Adding Interactivity

- **[Adding Interactivity](https://react.dev/learn/adding-interactivity)** (Overview)
  Overview of how state and events create interactive behavior.
- **[Responding to Events](https://react.dev/learn/responding-to-events)**  
  Attaching event handlers and React’s event system.
- **[State: A Component's Memory](https://react.dev/learn/state-a-components-memory)**  
  Understanding state and how it drives UI changes.
- **[Render and Commit](https://react.dev/learn/render-and-commit)**  
  How React processes updates: render → diff → commit.
- **[State as a Snapshot](https://react.dev/learn/state-as-a-snapshot)**  
  Why state updates are asynchronous and snapshot-based.
- **[Queueing a Series of State Updates](https://react.dev/learn/queueing-series-of-state-updates)**  
  How React batches updates and queues state transitions.
- **[Updating Objects in State](https://react.dev/learn/updating-objects-in-state)**  
  Immutable methods for updating object-based state.
- **[Updating Arrays in State](https://react.dev/learn/updating-arrays-in-state)**  
  Immutable patterns for array updates in state.

---

### Managing State

- **[Managing State](https://react.dev/learn/managing-state)** (Overview)
  High-level strategies for structuring and managing state.
- **[Reacting to Input with State](https://react.dev/learn/reacting-to-input-with-state)**  
  How form inputs interact with state to produce controlled components.
- **[Choosing the State Structure](https://react.dev/learn/choosing-the-state-structure)**  
  How to shape state for clarity, minimalism, and scalability.
- **[Sharing State Between Components](https://react.dev/learn/sharing-state-between-components)**  
  Lifting state up to coordinate multiple components.
- **[Preserving and Resetting State](https://react.dev/learn/preserving-and-resetting-state)**  
  When React preserves or resets component state and why.
- **[Extracting State Logic into a Reducer](https://react.dev/learn/extracting-state-logic-into-a-reducer)**  
  Using reducers for complex or multi-step state logic.
- **[Passing Data Deeply with Context](https://react.dev/learn/passing-data-deeply-with-context)**  
  Using React Context to avoid prop drilling.
- **[Scaling Up with Reducer and Context](https://react.dev/learn/scaling-up-with-reducer-and-context)**  
  Combining reducers and context for global or shared state management.

---

### Escape Hatches

- **[Escape Hatches](https://react.dev/learn/escape-hatches)** (Overview)
  Tools for handling non-declarative or advanced cases.
- **[Referencing Values with Refs](https://react.dev/learn/referencing-values-with-refs)**  
  Using refs to store mutable values without triggering renders.
- **[Manipulating the DOM with Refs](https://react.dev/learn/manipulating-the-dom-with-refs)**  
  Direct DOM access for imperative or low-level operations.
- **[Synchronizing with Effects](https://react.dev/learn/synchronizing-with-effects)**  
  Understanding effects, dependencies, cleanup, and synchronization.
- **[You Might Not Need an Effect](https://react.dev/learn/you-might-not-need-an-effect)**  
  Guidelines for reducing unnecessary effects and improving performance.
- **[Lifecycle of Reactive Effects](https://react.dev/learn/lifecycle-of-reactive-effects)**  
  How effects run, clean up, and re-run across renders.
- **[Separating Events from Effects](https://react.dev/learn/separating-events-from-effects)**  
  Why event-based logic should be separated from reactive effect logic.
- **[Removing Effect Dependencies](https://react.dev/learn/removing-effect-dependencies)**  
  Techniques for reducing dependency arrays and preventing infinite loops.
- **[Reusing Logic with Custom Hooks](https://react.dev/learn/reusing-logic-with-custom-hooks)**  
  How to extract reusable logic into custom hooks.
