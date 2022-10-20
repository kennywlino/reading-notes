# React and Forms

## Why this topic matters

    As we integrate HTML form elements into React, we need to find a way to maintain form element state with React state. Fortunately, there's an easy way to keep state consistent.

## Forms

Based on [React docs](https://reactjs.org/docs/forms.html).

1. What is a ‘Controlled Component’?

    A controlled component refers to input for elements that have their values maintained by a React component's state. This is because form elements like `<input>`, `<textarea>`, and `<select>` usually maintain their own state. Using a controlled component will allow us to maintain the input state in one location.

2. Should we wait to store the users responses from the form into state when they submit the form OR should we update the state with their responses as soon as they enter them? Why.

    We should update the state with their responses *as soon as* they enter them so React can be the source of truth. Otherwise there is potential for the form and React state value to differ.

3. How do we target what the user is entering if we have an event handler on an input field?
    The `handleChange` function on `input`'s `onChange` prop will update the state of `input`'s `value` on every keystroke.

## The Conditional (Ternary) Operator

Based on this [Medium article](https://codeburst.io/javascript-the-conditional-ternary-operator-explained-cac7218beeff).

1. Why would we use a ternary operator?

    A ternary operator allows us to write an `if` statement in one line.

2. Rewrite the following statement using a ternary statement:

    ```javascript
    if(x===y){
    console.log(true);
    } else {
    console.log(false);
    }
    ```

    ```javascript
    x === y ? true : false;
    ```

### Nesting operators

We can also nest ternary operators to chain multiple conditions.

Example from article:

```javascript
let isStudent = false;
let isSenior = true;
let price = isStudent ? 8 : isSenior ? 6 : 10
// false ? 8 : true ? 6 : 10
console.log(price);
// 6
```

Since isStudent is `false`, between in the first part of `isStudent ? 8 : isSenior`, `isSenior` will be selected. From there, since `isSenior` is `true`, `price` will be `6`.

### Multiple operations

Ternary can be used to run multiple operations as well.

Example from the article:

```javascript
let isStudent = true;
let price = 12;
isStudent ? (
  price = 8,
  alert('Please check for student ID')
) : (
  alert('Enjoy the movie')
);
```
