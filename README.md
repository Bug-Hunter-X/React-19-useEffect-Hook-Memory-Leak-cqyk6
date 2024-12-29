# React 19 useEffect Hook Memory Leak
This repository demonstrates a common error in React 19 involving the `useEffect` hook and how to fix it. The issue is a memory leak caused by an improperly handled `setInterval` within `useEffect`.

## Problem
The provided `MyComponent` uses `setInterval` to increment a counter every second. However, the interval is never cleared, leading to multiple intervals running concurrently.  This consumes memory and might cause unexpected behavior.  In older versions of React, this might not be immediately obvious, but in React 19 with stricter memory management, it could become increasingly problematic.

## Solution
The solution involves using the cleanup function provided by `useEffect` to clear the interval when the component unmounts or when the dependencies change.  The `return` statement within `useEffect` provides the cleanup mechanism.