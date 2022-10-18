# State and Props

## Why this topic matters

## React lifecycle

Answers based on this [Medium article](https://medium.com/@joshuablankenshipnola/react-component-lifecycle-events-cb77e670a093).

1. Based off the diagram, what happens first, the `render` or the `componentDidMount`?

    Based off the diagram, the `render` will happen first.

    ![React Lifecycle Events](https://miro.medium.com/max/1400/0*0saPKFiTUk6W3FYp) [^1]

    [^1]: Taken from the Medium article.

2. What is the very first thing to happen in the lifecycle of React?
    
    The constructor of the component will be called.

3. Put the following things in the order that they happen: `componentDidMount`, `render`, `constructor`, `componentWillUnmount`, `React Updates`

    `constructor`, `render`, `componentDidMount` `React Updates`, `componentWillUnmount`

4. What does `componentDidMount()` do?
    `componentDidMount()` is called after a component is mounted. It is the place to load something or `setState()` as necessary and should be paired with code to unmount in `componentWillUnmount()`. 

    This can be seen in the `Clock` example from the [React docs](https://reactjs.org/docs/state-and-lifecycle.html).

    ```javascript
    class Clock extends React.Component {
        constructor(props) {
            super(props);
            this.state = {date: new Date()};
        }

        componentDidMount() {
            this.timerID = setInterval(
            () => this.tick(),
            1000
            );
        }

        componentWillUnmount() {
            clearInterval(this.timerID);
        }

        tick() {
            this.setState({
            date: new Date()
            });
        }```

## React State Vs Props

1. What types of things can you pass in the props?

2. What is the big difference between props and state?

3. When do we re-render our application?

4. What are some examples of things that we could store in state?