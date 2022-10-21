# Thinking in React and Higher-Order Functions

## Why this topic matters

Thinking in React is because as applications get bigger in React, it becomes harder to know what parts should be made into its own component. It also becomes harder to decide what pieces of data should be maintained as props vs. state. 

Higher-order functions are important as they are useful for processing data. We also use them frequently with Array functions like map, reduce, filter, and forEach, so this helps us understand what is possibly happening under the hood.

## Thinking in React

Based on [React docs](https://reactjs.org/docs/thinking-in-react.html).

1. What is the single responsibility principle and how does it apply to components?

    The single responsibility principle says that a module should be responsible for doing only *one* thing. With components, if they get too big, they need to be broken down into smaller components.

2. What does it mean to build a ‘static’ version of your application?

    Building a 'static' version of your application refers to building without any interactivity. When building a 'static' version of your application, we would focus on integrating the data into the UI by passing it down to the components via props. 

3. Once you have a static application, what do you need to add?

    After getting the static application ready, the next thing to add is state so that we can have interactivity.

4. What are the three questions you can ask to determine if something is state?

    The three questions are:

    1. Is it passed in from a parent via props? -- probably not state
    2. Does it remain unchanged over time? -- probably not state
    3. Can you calculate it based on other props or state in the component?  -- it isn't state

5. How can you identify where state needs to live?

    We can identify where state needs to live by:

    - looking at all components that rely on that particular state
    - find a common component parent

## Higher-Order Functions

Based on chapter from [Eloquent JavaScript](https://eloquentjavascript.net/05_higher_order.html#h_xxCc98lOBK).

1. What is a “higher-order function”?

    A higher-order function is a function that work on other functions either by taking them in as a parameter or returning another function.

2. Explore the greaterThan function as defined in the reading. In your own words, what is line 2 of this function doing?

    Line 2 of this function is returning a boolean statement that says return whether m is greater than n.

    ```javascript
    // from the reading
    function greaterThan(n) {
        return m => m > n;
    let greaterThan10 = greaterThan(10);
    console.log(greaterThan10(11));
    // true
    }
    ```

3. Explain how either map or reduce operates, with regards to higher-order functions.

    With map, it can take a function and apply it to all elements of a given array. With higher-order functions, map would take in the `array` and `transform` function and `transform(element)` would be applied during a for loop and the value would be added to a new array to return after processing.

    ```javascript
    // from the reading
    function map(array, transform) {
        let mapped = [];
        for (let element of array) {
            mapped.push(transform(element));
        }
        return mapped;
        }
    ```
