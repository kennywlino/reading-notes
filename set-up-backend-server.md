# Setting up a back-end and connecting it to the front-end

## Tools needed

### Back-end

- `dotenv`:  Handles all of the environment variables such as database URLs, server URLS, and API keys
- `express`: Manages the HTTP requests between client and server
- `cors`: Middleware used to validate connections between client and server
- `mongoose`: an object data modeling (ODM) library used to create schema for our database and connect to our MongoDB instance
- Thunder Client: a VSCode Extension used to test RESTful actions to our server

### Front-end

- `React`

## CRUD vs. REST with our back-end tools

| CRUD       | Mongoose                    | REST     | Axios            | Express        |
| ---------- | --------------------------- | -------- | ---------------- | -------------- |
| **C**reate | `Model.create()`            | `POST`   | `axios.post`     | `app.post()`   |
| **R**ead   | `Model.find()`              | `GET`    | `axios.get()`    | `app.get()`    |
| **U**pdate |                             | `PUT`    |                  |                |
| **D**elete | `Model.findByIdAndDelete()` | `DELETE` | `axios.delete()` | `app.delete()` |

## Code

[Taken from [class demo](https://github.com/codefellows/seattle-code-301d90/blob/main/class-11/inclass-demo/)]

### Basic set-up with `GET` / Read

#### Back-end

This is what a basic back-end set up would look like with basic `GET` endpoints.

1. We need to bring in all of our required packages and set them up.

    When setting up our MongoDB URL, we should make sure to include the name of our database.

    ```javascript
    /// *** .env ***
    PORT=3001
    mongodb+srv://kennywlino:<mongoDB database_ID>@can-of-books.zr8tgpp.mongodb.net/<NAME OF DATABASE>?retryWrites=true&w=majority

    ```

    ```javascript
    // *** server.js ***

    'use strict';

    // Required packages
    require('dotenv').config();
    const express = require('express');
    const cors = require('cors');

    // bring in mongoose
    const mongoose = require('mongoose');

    // ** REQUIRE MY MODEL ***
    const Cat = require('./models/cat.js');

    // ***** FROM MONGOOSE DOCS *****
    mongoose.connect(process.env.DB_URL);

    const db = mongoose.connection;
    db.on('error', console.error.bind(console, 'connection error:'));
    db.once('open', function () {
    console.log('Mongoose is connected');
    });

    // USE
    // implement express
    const app = express();

    // middleware
    app.use(cors());

    // define PORT validate env is working
    const PORT = process.env.PORT || 3002;

    ```

2. We set up our endpoints. We also make sure we have Express listening on our `PORT`.

    ```javascript 
    // ENDPOINT: root
    app.get('/', (request, response) => {
    response.status(200).send('Welcome!');
    });

    // ENDPOINT: catch-all for non-existing links
    app.get('*', (request, response) => {
    response.status(404).send('Not availabe');
    });

    // ERROR
    app.use((error, request, response, next) => {
    response.status(500).send(error.message);
    });

    // LISTEN
    app.listen(PORT, () => console.log(`listening on Port ${PORT}`));
    ```

3. We set up our schema in `models/<modelName>.js` and export it.

    ```javascript

    // *** models/cat.js ***
    'use strict';

    const mongoose = require('mongoose');

    const { Schema } = mongoose;

    const catSchema = new Schema({
    name: { type: String, required: true },
    color: { type: String, required: true},
    spayNeuter: { type: Boolean, required: true },
    location: { type: String, required: true }
    });

    const CatModel = mongoose.model('Cat', catSchema);

    module.exports = CatModel;
    ```

4. We seed our database with test data to confirm everything is wotking as expected. `Model.create()` from Mongoose allows us to create a new document in our database.

    ```javascript
    // *** seed.js***
    'use strict';

    const mongoose = require('mongoose');

    require('dotenv').config();
    mongoose.connect(process.env.DB_URL);

    const Cat = require('./models/cat.js');

    async function seed() {
    // **name: {type: String, required: true},
    // **color: {type: String, required: true},
    // **spayNeuter: {type: Boolean, required: true},
    // **location: {type: String, required: true}

    await Cat.create({
        name: 'Pat the cat',
        color: 'black and white',
        spayNeuter: true,
        location: 'Seattle'
    });

    console.log('Pat the cat was created');

    await Cat.create({
        name: 'Ronald',
        color: 'orange and white',
        spayNeuter: true,
        location: 'Seattle'
    });

    console.log('Ronald was created');

    await Cat.create({
        name: 'Victor',
        color: 'tabby',
        spayNeuter: true,
        location: 'Rainbow Bridge'
    });

    console.log('Victor was created');

    mongoose.disconnect();
    }

    seed();
    ```

5. We add an endpoint to `GET` all of our documents.

    ```javascript
    // ENDPOINT - TO GET ALL CATS FROM THE DATABASE - SEND IT TO OUR FRONT END

    app.get('/cats', getCats);

    async function getCats(request, response, next){
    try {
        let results = await Cat.find();

        response.status(200).send(results);
    } catch (error) {
        next(error);
    }
    }
    ```

#### Front-end

In order to integrate our server into our database, we can simply `GET` the data via our database URL and endpoint.

```javascript

// basic React aet-up
import React from 'react';
import './App.css';
import axios from 'axios';


class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      cats: [],
    }
  }

  // adding GET functionality
  getCats = async () => {
    try {
      // make a call to my server/cats to get cats
      let catData = await axios.get(`${process.env.REACT_APP_SERVER}/cats`);
      // catData.data
      this.setState({
        cats: catData.data
      });

    } catch (error) {
      console.log('we have an error: ', error.response);
    }
  }

  // REACT LIFECYCLE METHOD - FUNCTION WILL RUN AS SOON AS COMPONENT IS ADDED TO THE DOM TREE
  componentDidMount() {
    this.getCats();
  }

  render() {
    console.log('App State >>>', this.state);
    let cats = this.state.cats.map(cat => {
      return <p key={cat._id}>{cat.name} is a {cat.color} cat</p>
    })
    return (
      <>
        <header>
          <h1>Cool Cats</h1>
        </header>
        <main>
        {// if there are any cats render them}
          {
            this.state.cats.length > 0 &&
            <>
              {cats}
            </>
          }
        </main>
      </>
    );
  }
}

export default App;

```

### Creating / `ADD` functionality

#### Back-end

1. We need to add a JSON body parser since we will be working with JSON data.

    ```javascript
    // *** server.js ***
    ...

    // implement express
    const app = express();

    app.use(cors());

    // ADDING: express.json() is our JSON body parser
    app.use(express.json());

    const PORT = process.env.PORT || 3002;
    
    ...
    ```

2. We add a new endpoint.

    ```javascript
    // ENDPOINT TO ADD CATS
    app.post('/cats', postCats);

    async function postCats(request, response, next){
        try {
            let createdCat = await Cat.create(request.body);
            response.status(200).send(createdCat);
        } catch (error) {
            next(error);
        }
    }
    ```

#### Front-end

1. Add a form for users to fill out values for our data.

    ```javascript
    import React from 'react';
    import './App.css';
    import axios from 'axios';
    import Cats from './Cats.js';
    import { Button, Container, Form } from 'react-bootstrap';

    class App extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
        cats: [],
        }
    }

    ...

    render() {
        return (
        <>
            <header>
            <h1>Cool Cats</h1>
            </header>
            <main>
            <Container className="mt-5">
                <Form onSubmit={this.handleCatSubmit}>
                <Form.Group controlId="name">
                    <Form.Label>Name</Form.Label>
                    <Form.Control type="text" />
                </Form.Group>
                <Form.Group controlId="color">
                    <Form.Label>Color</Form.Label>
                    <Form.Control type="text" />
                </Form.Group>
                <Form.Group controlId="location">
                    <Form.Label>Location</Form.Label>
                    <Form.Control type="text" />
                </Form.Group>
                <Form.Group controlId="spayNeuter">
                    <Form.Check type="checkbox" label="spay-neuter" />
                </Form.Group>
                <Button type="submit">Add Cat</Button>
                </Form>
            </Container>
            </main>
        </>
        );
    }
    ```

2. Add a handler for the submit.

    ```javascript
    // *** app.js ***

    handleCatSubmit = (event) => {
        event.preventDefault();
        let newCat = {
        name: event.target.name.value,
        color: event.target.color.value,
        spayNeuter: event.target.spayNeuter.checked,
        location: event.target.location.value
        }
        console.log(newCat);

        // post my cat to my DB - another handler
        this.postCats(newCat);
    }

    postCats = async (newCatObj) => {
        try {
        let url = `${process.env.REACT_APP_SERVER}/cats`;

        let createdCat = await axios.post(url, newCatObj);
        
        this.setState({
            cats: [...this.state.cats, createdCat.data]
        })
        
        } catch (error) {
        console.log(error.message);
        }
    }
    ```

### `DELETE` functionality

With `DELETE`, we need to use the ID values in the URL to find the item we want to delete.

The structure of the URL would look like:

`http://api-website.com/search/ <ID VALUE> ? key=<VALUE> & anotherKey=<anotherValue>`

On the back-end, the ID would be referenced via `request.params.<nameOfIDValue>`.

#### Back-end

1. Add a `DELETE` endpoint.

    ```javascript
    // ENDPOINT TO DELETE CATS
    // we must have path parameter.
    // we will use a variable to capture that id
    // to create that variabble we add ':<variable-name>' in place of the path value
    
    app.delete('/cats/:catID', deleteCats);

    async function deleteCats(request,response, next){
        console.log(request.params);
        console.log(request.params.catID);
        try {
            let id = request.params.catID;
            await Cat.findByIdAndDelete(id);
            response.status(200).send('Cat was deleted');
        } catch (error) {
            next(error);
        }
    }
    ```

#### Front-end

The front-end is variable based on our component set-up, but this is how we did it in the demo.

1. We need to define a handler.

    ```javascript
     deleteCats = async (id) => {
        try {
        let url = `${process.env.REACT_APP_SERVER}/cats/${id}`;

        await axios.delete(url);

        let updatedCats = this.state.cats.filter(cat => cat._id !== id);

        this.setState({
            cats: updatedCats
        });

    ```

2. We pass the handler down to the `Cats` component.

    ```javascript
    render() {
        return (
        <>
            <header>
            <h1>Cool Cats</h1>
            </header>
            <main>
            {
                this.state.cats.length > 0 &&
                <>
                <Cats 
                cats={this.state.cats}
                handleDelete={this.deleteCats}
                />
                </>
            }
        ... 

    ```

3. The `Cats` component takes the handler in to pass down to each individual `Cat` component. When the `Delete` button is clicked on the `Cat` item, that specific `Cat` will pass its ID and call the handler. The anonymous function is added to prevent the handler from being called immediately.

    ```javascript
    import { Component } from 'react';
    import { Container, ListGroup, Button } from 'react-bootstrap';

    class Cats extends Component {
        render() {
            let cats = this.props.cats.map(cat => (
            <Cat cat={cat} key={cat._id} handleDelete={this.props.handleDelete}/>
            ))
            return (
            <Container>
                <ListGroup>
                {cats}
                </ListGroup>
            </Container>
            )
        }
    }

    class Cat extends Component {

    render() {
        console.log(this.props.cat);
        return (
        <ListGroup.Item>
            {this.props.cat.name} is {this.props.cat.color} cat
            <Button variant="dark" onClick={() => {this.props.handleDelete(this.props.cat._id)}}>Delete</Button>
        </ListGroup.Item>
        )
     }
    }

    export default Cats;

    ```
