# d3-rosetta
Maximize framework interoperability for interactive graphics

WORK IN PROGRESS - NOT READY FOR USE

## The Problem: Re-use D3-based logic in component frameworks

React, Svelte, Vue, Angular and other frameworks provide various solutions for state management and DOM manipulation. D3 provides data transormation utilities for data visualization and other uses, and can also manipulate the DOM. When a technical challenge in interactive data visualization is solved, ideally that solution an be re-used across various frameworks, thus avoiding the need to re-implement the solution multiple times for multiple frameworks. This is why `d3-rosetta` exists.

## Unidirectional Data Flow

One pattern that can be invoked cleanly from multiple frameworks is that of unidirectional data flow. In this paradigm, a single monolithic function is responsible for updating the DOM or otherwise rendering pixels based on updates to a single monolithic state. A similar pattern is commonly seen in React logic with a combination of `useState` and `useEffect`. A simple implementation of unidirectional data flow works well for small problems, but as complexity scales, a need arises for performance optimization.

## Memoization

The pattern of unidirectional data flow includes a single monolithic function that executes every time state changes. Therefore, it is likely that not all of the internals of that function must execute on each and every update to the state. Especially for relatively expensive computations like data processing (e.g. filtering or aggregation), it makes sense to avoid recomputing the same derived values unnecessarily. This is the problem solved by memoization.

In React, memoization can be achieved with the `useMemo` hook. The `d3-rosetta` library introduces a similar construct for memoization based on the idea of storing memoized values on the DOM. This approach makes the utility compatible with hot reloading, wherein new code is injected at runtime. If the memoized values were stored in a JavaScript closure, they would be lost on each hot reload. Here's how this memoization utility can be used:

```js
```
