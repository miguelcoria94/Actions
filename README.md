<h1 align='center'>
Actions
</h1>

Actions are the only way to trigger changes to the store's state.

Actions are simple POJOs with a mandatory type key and optional payload keys containing new info.

Actions get sent using store.dispatch() and are the primary drivers of the Redux loop.

<h1 align='center'>
Using action creators
</h1>

When an action is dispatched, any new state data must be passed along ad the payload.

The example below passed a payload key of fruit with the new state data. 'orange':

```js
    const addOrange = {
        type: "ADD_FRUIT",
        fruit: 'orange',
    }

    store.dispatch(addOrange);
    console.log(store.getState()); // ['orange']
```

However, when these action payloads are generated dynamically, it becomes necessary to extrapolate the creation of the action object into a function.

These functions are called action creators.

The JavaScript objects they return are the actions.

To initiate a dispatch, you pass the result of calling an action creator to store.dispatch()

For Example, an action creator function to create "ADD_FRUIT" action looks like this:

```js
    const addFruit = (fruit) => {
            type: "ADD_FRUIT",
            fruit,
    }
```

Now we can add any fruit to the store using our action creator addFruit(fruit), instead of having to define an object for each fruit:

```js
    store.dispatch(addFruit('apple'));
    store.dispatch(addFruit('strawberry'));
    store.dispatch(addFruit('lychee'));
    console.log(store.getState()); // [ 'orange', 'apple', 'strawberry', 'lychee' ]
```

<h1 align='center'>
Preventing typos in action type string literals
</h1>

Update your actions to include 'ADD_FRUIT', 'ADD_FRUITS', 'SELL_FRUIT', and 'SELL_OUT':

```js
    const ADD_FRUIT = 'ADD_FRUIT';
    const ADD_FRUITS = 'ADD_FRUITS';
    const SELL_FRUIT = 'SELL_FRUIT';
    const SELL_OUT = 'SELL_OUT';

    const addFruit = (fruit) => ({
    type: ADD_FRUIT,
    fruit,
    });

    const addFruits = (fruits) => ({
    type: ADD_FRUITS,
    fruits,
    });

    const sellFruit = (fruit) => ({
    type: SELL_FRUIT,
    fruit,
    });

    const sellOut = () => ({
    type: SELL_OUT,
    });
```

Cnstants are used for all the fruit action types.

This is to prevent simple typos in the reducers case clauses

<h1 align='center'>
Reviewing a completed Fruit Stand example
</h1>


Check repo folder
