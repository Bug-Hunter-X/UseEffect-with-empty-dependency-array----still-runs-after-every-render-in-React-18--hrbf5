# React 18+ useEffect Behavior Change

This repository demonstrates a subtle change in how `useEffect` with an empty dependency array (`[]`) behaves in React 18 and later versions.

In previous versions, an empty dependency array ensured that the effect only ran once after the initial render.  However, in React 18+, if the component re-renders due to changes elsewhere in the component tree (even if the state/props the effect directly depends on haven't changed), the effect will still re-run.  This can lead to unexpected behavior and performance issues.

## Bug Description

The provided `bug.js` demonstrates an effect that logs a message.  Even though the `count` state is not directly used in the effect, the effect still runs on every render.  This is counter-intuitive and might not be what developers expect.

## Solution

The `bugSolution.js` file provides a fix.  The key is to add a check within the effect to make sure that the effect only runs if the value of count has actually changed. This is important to prevent the effect from running unnecessarily and leading to performance issues.

## How to run the code

1. Clone the repo
2. Navigate to the project directory
3. Run `npm install`
4. Run `npm start`

The app will run on `localhost:3000`