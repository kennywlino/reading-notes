# More CRUD

## Why this topic matters

Understanding the relationshup between REST and CRUD will allow us to create a better mental model of our databases.

## CRUD Basics

Based on [this article](https://medium.com/geekculture/crud-operations-explained-2a44096e9c88).

1. Which HTTP method would you use to update a record through an API?

    We would use the `PUT` method to update a record.

2. Which REST methods require an ID parameter?

    The Update and Delete methods require an ID parameter. Their route would look like `/books/:bookID`.

## Speed Coding: Building a CRUD API

Based on [this video](https://www.youtube.com/watch?v=EzNcBhSv1Wo).

1. What’s the relationship between REST and CRUD?

    The relationship between REST and CRUD is that CRUD describes the basic operations we can do with a database, while REST refers to the way we can manage data with resources defined via URLs and endponts (e.g. HTTP).

2. If you had to describe the process of creating a RESTful API in 5 steps, what would they be?

    In order to create a RESTful API we need to add methods for:

    1. POST
    2. PUT
    3. PATCH
    4. GET
    5. DELETE

## Things I want to know more about
