# React UseEffect setInterval Memory Leak

This repository demonstrates a common mistake in React: using `setInterval` within the `useEffect` hook without proper cleanup. This leads to memory leaks as the interval continues to run even after the component unmounts.

## Bug Description

The `MyComponent` uses `setInterval` to update a counter every second. However, it lacks the cleanup function in `useEffect` to stop the interval when the component is unmounted. This results in multiple intervals running concurrently if the component is remounted.

## Solution

The solution involves using the return value of `useEffect` to implement the cleanup function. This function is called when the component unmounts or when the dependencies change, ensuring that `clearInterval` is called to stop the interval.  See `bugSolution.js` for the corrected code.

## How to reproduce the bug

Clone this repository and run `npm start` to see the component in action.  Observe the memory usage in your browser's developer tools.  If the component is repeatedly mounted and unmounted, you'll notice a gradual increase in memory usage. This is a clear indication of a memory leak.