# React useEffect Missing Dependency

This example demonstrates a common error in React's `useEffect` hook: a missing dependency in the dependency array. This can lead to unexpected behavior, such as infinite loops or incorrect updates.

## The Problem

The `useEffect` hook is used to perform side effects, such as setting up timers or fetching data. The second argument to `useEffect` is an array of dependencies. React only re-runs the effect if any of the dependencies change.

In this case, the `setInterval` function is called inside the `useEffect` hook, but the dependency array is empty (`[]`). This means that the effect will run only once on mount, but the `setInterval` will keep updating `count`, causing an infinite loop because `useEffect` never re-runs (it would if `count` was in the dependency array). 

## The Solution

The solution is to include `count` in the dependency array. This ensures that the effect is only triggered when the `count` changes.