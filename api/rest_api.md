# REST API
REST API (Representational State Transfer Application Programming Interface) is a set of principles and architectural constraints for designing and interacting with web services. It's a way for different software applications to communicate with each other over the internet using standard HTTP methods.

How a REST API works:

- Resources: In a RESTful API, data is represented as resources. Each resource is identified by a unique URL, and it can be accessed and manipulated using standard HTTP methods.

- `HTTP Methods:`
    GET: Retrieve a resource's data.
    POST: Create a new resource.
    PUT: Update an existing resource or create it if it doesn't exist.
    DELETE: Delete a resource.

- `Request and Response:`
    Clients send HTTP requests to the server using methods like GET, POST, PUT, and DELETE.
    Servers respond with HTTP status codes and data, usually in JSON or XML format.

- `Statelessness:` The server doesn't maintain information about the client's state between requests. Each request is independent, containing all the necessary information.

Un`iform Interface:` APIs follow a consistent structure and use standardized HTTP methods, making them easy to understand and work with.

- `Hypermedia as the Engine of Application State (HATEOAS):` RESTful APIs can include links in responses, guiding clients to related resources and actions.