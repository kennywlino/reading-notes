# API Design Best Practices

## Why this topic matters

This topic is important as we design our own APIs as the purpose of APIs are to have consistent data representations and requests across the web. Organizing our assets within the API also can get difficult without having a structure to how to expose the data via the API. Emphasizing that the data should be organized via the resources (nouns) helps us establish consistency.

## API Design Best Practices

Based on [this Microsoft article](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design).

1. What does REST stand for?

    It stands for REpresentational State Transfer.

2. REST APIs are designed around *resources*.

    Resources can be any kind of object, data or service.

3. What is an identifier of a resource? Give an example.

    The identifier of a resource is a uniform resource identifier (URI). It is unique to that identifier.

    Example:

    ```javascript
    http:/example.com/account/1
    ```

4. What are the most common HTTP verbs?

    The most common HTTP verbs are `GET`, `POST`, `PUT`, `PATCH`, `DELETE`.

5. What should the URIs be based on?

    URIs should be based on the nouns (i.e .the resources) instead of verbs (the actions taken on the resources). They should also be plural nouns if they represent collections.

6. Give an example of a good URI.

    ```javascript
    http://example.com/orders // Nouns - Good
    
    http://example.com/create-order // Verbs - Bad
    ``` 

7. What does it mean to have a ‘chatty’ web API? Is this a good or a bad thing?

    A 'chatty' web API is an API that needs to make multiple requests to collect all of the data it needs because the data is split into a more resources (i.e. links). This is not a good thing as the more requests we make, the bigger the load gets.

8. What status code does a successful GET request return?

    A successful GET request usually returns HTTP status code 200.

9. What status code does an unsuccessful GET request return?

    An unsuccessful GET request should return HTTP status code 404 (Not found).

10. What status code does a successful POST request return?

    A successful POST request should return HTTP status code 201 (Created).

11. What status code does a successful DELETE request return?

    A successful DELETE request should return HTTP status code 204 (No content).

## Things I want to know more about