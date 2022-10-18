# Introduction to React and Components

## Why this topic matters

React allows us to create components to create our UIs. Because components are reusable and modular, they can help us write much more organized code without having repetitive code.

## Component-Based Architecture
Answers based on this [tutorialspoint article](https://www.tutorialspoint.com/software_architecture_design/component_based_architecture.htm).

1. What is a "component"?

    A component is a portion of code that describes a well-defined function designed to be flexible and reusable and used as a part of a higher-level interface. They work in conjunction with other components to define a larger functionality. 

2. What are the characteristics of a component?

    Components are:

    * reusable -- can be reused in various tasks
    * replaceable -- can be replaced with similar components
    * context-free -- not limited to one environment or task
    * extensible -- can have extended features from other components for new behaviors
    * encapsulated -- does not expose internal process, data or state
    * independent -- little to no dependencies on other components

3. What are the advantages of using component-based architecture?

    There are many advantages of using component-based architecture such as the ease of deployment, lowered costs, and reliability. This is because components allow us to organize code in an effective way, allowing us to reuse code or modify certain elements without affecting the system as a whole.


## Props in React
Answers based on this [ITNEXT article](https://itnext.io/what-is-props-and-how-to-use-it-in-react-da307f500da0#:~:text=%E2%80%9CProps%E2%80%9D%20is%20a%20special%20keyword,way%20from%20parent%20to%20child).

1. What is "props" short for?

    Props is short for properties.

2. How are props used in React?

    Props are assigned much like attributes and values with HTML tags.
    `<ChildComponent text={"I'm the 1st child"} />`

    When writing the function, props can be passed as function arguments and accessed with dot notation.

    ```javascript
    const ChildComponent = (props) => {
      return <p>{props.text}</p>;
    }
    ```

3. What is the flow of props?

    Props move in a uni-directional flow from parent to child.

## Things I want to know more about