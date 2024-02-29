# @elastik/reduce-reducers

[![Build Status](https://travis-ci.org/best-performance/reduce-reducers.svg?branch=master)](https://travis-ci.org/best-performance/reduce-reducers)
[![npm Version](https://img.shields.io/npm/v/@elastik/reduce-reducers.svg)](https://www.npmjs.com/package/@elastik/reduce-reducers)
[![npm Downloads Monthly](https://img.shields.io/npm/dm/@elastik/reduce-reducers.svg)](https://www.npmjs.com/package/@elastik/reduce-reducers)

> Reduce multiple reducers into a single reducer from left to right

## NOTE

This is a fork of [reduce-reducers](https://github.com/redux-utilities/reduce-reducers.git), simply with the dependabot updates merged, and republished as `@elastik/reduce-reducers`

## Install

```sh
npm install @elastik/reduce-reducers
```

## Usage

```js
import reduceReducers from '@elastik/reduce-reducers';

const initialState = { A: 0, B: 0 };

const addReducer = (state, payload) => ({ ...state, A: state.A + payload });
const multReducer = (state, payload) => ({ ...state, B: state.B * payload });

const reducer = reduceReducers(initialState, addReducer, multReducer);

const state = { A: 1, B: 2 };
const payload = 3;

reducer(state, payload); // { A: 4, B: 6 }
```

## FAQ

### Why?

Originally created to combine multiple Redux reducers that correspond to different actions (e.g. [like this](https://github.com/acdlite/redux-fsa/blob/master/src/handleActions.js#L12)). Technically works with any reducer, not just with Redux, though I don't know of any other use cases.

### What is the difference between `reduceReducers` and `combineReducers`?

This StackOverflow post explains it very well: [https://stackoverflow.com/a/44371190/5741172](https://stackoverflow.com/a/44371190/5741172)
