# CRUD

## Why this topic matters

Understanding status codes and how to specify certain results given from the server is important as we build out our own RESTful applications.

## Status Codes Based on REST Methods

Based on this [blog post](https://www.moesif.com/blog/technical/api-design/Which-HTTP-Status-Code-To-Use-For-Every-CRUD-App/).

1. In your own words, describe what each group of status code represents:

    100s = Informational status codes -- The header part of the request was received and the server is working on a transmission demand from the client.
    200s = Success codes -- The request was accepted.
    300s = Redirection codes -- The resource isn't available at the expected location.
    400s = Client error codes -- An invalid request was made.
    500s = Server error codes -- Errors with the server included overwhelmed servers or unreachable servers.

2. What is a status code 202?

    Status code 202 is for **Accepted** and is used often to indicate *asynchronous* processing, i.e. the process will finish later.

3. What is a status code 308?

    Status code 308 is for **Permanent Redirect** and is used to tell the client to that the current URL should no longer be used and to use the new given URL.

4. What code would you use if an update didn’t return data to a client?

    We can use code 204 for **No Content**.

5. What code would you use if a resource used to exist but no longer does?

    We can use code 410 for **Gone**.

6. What is the ‘Forbidden’ status code?

    The status code for **Forbidden** is 403. This code indicates that the client has given necessary info to authorize itself, but still does not have the appropriate permissions to access the resource.

## Build A REST API With Node.js, Express, & MongoDB

Based on this [video](https://www.youtube.com/channel/UCFbNIlppjAuEX4znoulh0Cw).

1. Why do we need to pull our MongoDB database string out of our server and put it into our .env?

    We need to pull our MongoDB database string and put it in our .env because we won't be running the database on localhost when we deploy.

2. What is middleware?

    Middleware is code that runs when the server receives the request, but before it's passed to the routes.

3. What does app.use(express.json()) do?

    `app.use(express.json())` allows our server to accept JSON as the body of a request instead of a `POST` or `GET`.

4. What does the /:id mean in a route?

    `/:id` means that it is a parameter to the request and can be accessed with `req.params.id`.

5. What is the difference between PUT and PATCH?

    `PUT` would update all of the information for the selected item vs `PATCH` which only updates on the information passed.

6. How do you make a default value in a schema?

    In order to make a default value in a schema, we can add `default: ` in the object for any schema item.

    ```javascript
    const forumSchema = new mongoose.Schema({
        name: {
            type: String,
            required: true
        },
        postDate: {
            type: Date,
            required: true,
            default: Date.now
        }
    })
    ```

7. What does a 500 error status code mean?

    A 500 error status code means that there was an error with our server and *not* with the user or client.

8. What is the difference between a status 200 and a status 201?

    Status 201 is a more specific status code that means that an object was successfully created, while 200 just means successful.

## Things I want to know more about
