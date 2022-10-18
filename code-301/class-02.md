# State and Props

## Why this topic matters

State and props are both ways that React can manage our data and make our components more reusable. However, state and props are used in different ways where state manages our dynamic data, and props manages our static data.

As we've seen, examples of props include passing in names or subtitles while state can be things like a clock which constantly is updating.

## React lifecycle

Answers based on this [Medium article](https://medium.com/@joshuablankenshipnola/react-component-lifecycle-events-cb77e670a093).

1. Based off the diagram, what happens first, the `render` or the `componentDidMount`?

    Based off the diagram, the `render` will happen first.

    ![React Lifecycle Events](https://miro.medium.com/max/1400/0*0saPKFiTUk6W3FYp)

    (Diagram taken from Medium article.)

2. What is the very first thing to happen in the lifecycle of React?
    
    The constructor of the component will be called.

3. Put the following things in the order that they happen: `componentDidMount`, `render`, `constructor`, `componentWillUnmount`, `React Updates`

    `constructor`, `render`, `componentDidMount`, `React Updates`, `componentWillUnmount`

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
        }
    ```

## React State Vs Props

Answers based off [this video](https://www.youtube.com/watch?v=IYvD9oBCuJI).

1. What types of things can you pass in the props?

    We can pass in any sort of static element in `props`. In the video, Kyle mentions that we can pass in an initialization value for things like a Counter. We can also pass in titles, subtitles, etc. to create static text.

2. What is the big difference between props and state?

    The big difference is that `props` comes from *outside* a component and must be updated *outside*, while `state` is managed *inside* the component and is updated *inside*. 

3. When do we re-render our application?

    We re-render our application when we `setState()`.

4. What are some examples of things that we could store in state?
    Some examples include:
        - a counter
        - time
        - Forms (input, checkbox, etc.)

## Things I want to know more about

I'm curious to know when we would set shouldComponentUpdate() to `false` vs. relying solely on props.