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

2. List 4 things that the spread operator can do.

    It can:
        - use arrays as arguments
        - make adding state to React easier
        - copy an array
        - convert NodeList to an array

3. Give an example of using the spread operator to combine two arrays.

    ```javascript
    const arr1 = ['a', 'b', 'c'];
    const arr2 = ['d', 'e', 'f'];
    const combined = [...arr1, ...arr2];
    console.log(combined);
    // combined = ['a', 'b', 'c', 'd', 'e', 'f'];
    ```

4. Give an example of using the spread operator to add a new item to an array.

    ```javascript
    const arr1 = ['a', 'b', 'c'];
    const arr2 = ['d', 'e', 'f', ...arr1];
    console.log(arr2);
    // arr2 = ['a', 'b', 'c', 'd', 'e', 'f'];
    ```

5. Give an example of using the spread operator to combine two objects into one.

    ```javascript
    const obj1 = {a: 1, b: 2, c: 3};
    const obj2 = {d: 4, e: 5, f: 6};
    const obj3 = {...obj1, ...obj2};
    console.log(obj3);
    // obj = {a: 1, b: 2, c: 3, d: 4, e: 5, f: 6}
    ```

## How to Pass Functions Between Components

Based on this [video](https://www.youtube.com/watch?v=c05OL7XbwXU).

1. In the video, what is the first step that the developer does to pass functions between components?

2. In your own words, what does the increment function do?

    ```javascript
    // from the video
    increment = (name) => {
        let ppl = this.state.people.map ( (p) => {
            if(p.name === name) {
                p.count++;
            }
            return p;
        })
    }
    ```

    The increment function takes in a `name` and takes `people` from the `state` object and maps it to a new array `ppl`. The `map` function iterates over each object `p` from `people` and will increment `+` the `count` of that object if the `p.name` matches `name`.

3. How can you pass a method from a parent component into a child component?

    To pass a method from a parent component into a child component, we can simply pass it in like another prop.

    ```javascript
    class App extends React.Component {
    ...

    increment = () => {};

    ...

   <Person 
    name={person.name}
    count={person.count}
    increment={this.increment}
    />
    ```

4. How does the child component invoke a method that was passed to it from a parent component?

    The child component can invoke a method that was passed to it from a parent component by calling `this.props.<methodName>`. 

    ```javascript
    // from the video
    increment = (ev) = {
        ev.preventDefault();
        this.setState({hasChanged:true});

        this.props.increment(this.props.name);
    }
    ```

    ## Things I want to know more about
