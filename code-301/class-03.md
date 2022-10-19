# Passing Function as Props

## Why this topic matters

## List and keys

Based on [React Docs](https://reactjs.org/docs/lists-and-keys.html).

1. What does .map() return?

    .map() returns a new array.

    ```javascript
    const words = ['hello', 'goodbye', 'yes', 'no'];
    const exclaimedWords = words.map((word) => word + '!');
    // exclaimedWords = ['hello!', 'goodbye!', 'yes!', 'no!'];
    ```

2. If I want to loop through an array and display each value in JSX, how do I do that in React?

    We need to wrap the value in curly braces `{}`.

    ```javascript
    const words = ['hello', 'goodbye', 'yes', 'no'];
    const wordsHeaders = words.map((word) =>
        <h1>{word}</h1>
    );
    ```

3. Each list item needs a unique **key**.

4. What is the purpose of a key?
    The purpose of a key is to help React know what items have been modified.

## The Spread Operator

Based on this [Medium article](https://medium.com/coding-at-dawn/how-to-use-the-spread-operator-in-javascript-b9e4a8b06fab) and [JavaScript.info article](https://javascript.info/rest-parameters-spread).

1. What is the spread operator?

    The spread operator is used to take an iterable object (e.g. an array)`and expand its elements into a list of arguments.

    ```javascript
        // Math functions tend to need the numbers as args
        Math.max([2, 4, 6]); // NaN
        Math.max(...[2, 4, 6]) // 6
    ```

2.List 4 things that the spread operator can do.

    It can:
        - use arrays as arguments
        - make adding state to React easier
        - copy an array
        - convert NodeList to an array

3. Give an example of using the spread operator to combine two arrays.

4. Give an example of using the spread operator to add a new item to an array.

5. Give an example of using the spread operator to combine two objects into one.

