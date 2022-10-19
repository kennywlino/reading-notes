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
