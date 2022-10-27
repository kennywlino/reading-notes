# Functional Progamming Concepts and Node.js Modules and require()

## Why this topic matters

Functional progamming is relevant as we learn more programming theory. Arrow functions are a form of functional programming that we use that follows the concept of a `pure function`, and helps us to write more concise code. 

Modules are important as we write larger programs. Knowing how to separate our code into different modules will allow us to keep our code base more organized.

## Functional Progamming Concepts

Based on this [Medium article](https://medium.com/the-renaissance-developer/concepts-of-functional-programming-in-javascript-6bc84220d2aa).

1. What is functional programming?

    Functional programming is a style of prgraomming that structures code as mathematical functions and centers around not changing state or mutating data.

2. What is a pure function and how do we know if something is a pure function?

    A pure function is a function that **always** returns the same result with the same arguments. It should also not create any side effects.

3. What are the benefits of a pure function?

    Testing pure functions is more straightforward. We know that with a paramater `A`, it will give us a value `B`, and with a parameter `X`, it will give us a value `Y`.

4. What is immutability?

    Immutability is when data is unchanging / cannot be changed. In order to change an immutable object, we have to create a new object with the change.

5. What is Referential transparency?

    Referential transparency is when a function **consistently** gives us the same result for the same parameters. The author says:

    `pure functions + immutable data = referential transparency`

## Node.js Modules and require()

Based on this [The Net Ninja video](https://www.youtube.com/watch?v=xHLd36QoS4k).

1. What is a module?

    A module is a piece of code that has a certain functionality separated out to a different JavaScript file.

    For example, we could have a `calculate.js` to hold a calculate function, and `app.js` to hold our main functionalities.

2. What does the word ‘require’ do?

    `require` allows us to use the functionality of a module by passing in its path.

3. How do we bring another module into the file the we are working in?

    We bring it in by:

    ```javascript
    require('./calculate');
    ```

4. What do we have to do to make a module available?

    In order to make a module available outside, we need to add:

    ```javascript
    modules.exports = counter;
    ```

    This is because when we use `require()`, it looks for whatever the `module.exports` property is set to.

## Things I want to know more about
