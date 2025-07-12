[Source:Postman API Fundamentals Student Expert certification ](https://academy.postman.com/path/postman-api-fundamentals-student-expert/postman-api-fundamentals-student-expert-certification-1)

An **Application Programming Interface (API)** is a contract that allows code to talk to other code. APIs are the building blocks of modern software because they allow for sharing of resources and services across applications, organizations, and devices.
### Why are APIs important?

1. APIs help developers **integrate exciting features** and **build automation** without reinventing the wheel  
    _ex: using a Weather API instead of launching your weather balloons_  
      
    
2. APIs allow enterprises to **open up their product for faster innovation  
    **_ex: apps that interact with Twitter or Meta APIs by posting on your behalf or reading tweets_  
      
    
3. APIs can **be products themselves**  
    _ex: Software as a Service (SaaS) products like Stripe's payment APIs or Twilio's text messaging and email APIs_

You can think of APIs as being like a waiter at a restaurant, serving as a go-between for the customer and the kitchen. A customer who wants soup doesn't go into the kitchen to cook. They don't even have to know how to make soup! They only have to know _how to ask_ _the waiter_ for soup_, expecting the waiter to_ bring back soup_._

|   |   |   |
|---|---|---|
|**Networking term**|**Description**|**Restaurant analogy**|
|Client|The requester. _Ex: browser, web app, mobile app_|Customer|
|API|Simplified interface for interacting with the backend|Waiter|
|Server|The backend where the processing happens|Kitchen|
## Types of APIs

- **Hardware APIs**  
    Interface for software to talk to hardware.  
    _Example: How your phone's camera talks to the operating system._ 
- **Software Library APIs  
    **Interface for directly consuming code from another code base.  
    _Example: Using methods from a library you import into your application.  
      
    _
- **Web APIs  
    **Interface for communicating across code bases over a network.  
    _Example: Fetching current stock prices from a finance API over the internet._

Multiple API types may be used to achieve a task. For example, uploading a photo to Instagram makes use of various APIs:

1. Hardware API for the app to talk to your camera  
      
    
2. Software library API for the image to be processed with filters  
      
    
3. Web API for sending your image to Instagram's servers so your friends can like it!

### Architectures
There is more than one way to build and consume APIs. Some architecture types you may come across are:

- REST (Representational State Transfer)
- GraphQL
- WebSockets
- webhooks
- SOAP (Simple Object Access Protocol)
- gRPC (Google Remote Procedure Call)
- MQTT (MQ Telemetry Transport)

### Access

APIs also vary in the scope of who can access them.  

- **Public APIs (aka Open APIs)  
    **Consumed by anyone who discovers the API  
      
    
- **Private APIs  
    **Consumed only within an organization and not made public  
      
    
- **Partner APIs  
    **Consumed between one or more organizations that have an established relationship

### Make your first request.

Set the request method to **GET**, and the **request URL** to `GET` `https://library-api.postmanlabs.com/books`
### View the response
If everything goes well, you will see a response from the server in the lower half of Postman.  
  
It should look like this: a [JSON](https://www.w3schools.com/whatis/whatis_json.asp) (JavaScript Object Notation) response body with an **array** of book **objects**. You can scroll down to see more books.

### Request methods
When we make an HTTP call to a server, we specify a **request method** that indicates the type of operation we are about to perform. These are also called **HTTP verbs**.  
  
Some common HTTP request methods correspond to the CRUD operations mentioned earlier. You can see a list of more methods [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods).  

|                 |                                                                                                                               |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Method name** | **Operation**                                                                                                                 |
| `GET`           | Retrieve data (**R**ead)                                                                                                      |
| `POST`          | Send data (**C**reate)                                                                                                        |
| `PUT/PATCH`     | Update data (**U**pdate)  <br>  <br>`PUT` usually replaces an entire resource, whereas `PATCH` usually is for partial updates |
| `DELETE`        | Delete data (**D**elete)                                                                                                      |

Since we are "getting" books and not modifying any data, it makes sense that we are making a `GET` request.

### Request URL

In addition to a request method, a request must include a **request URL** that indicates _where_ to make the API call. A request URL has three parts: a **protocol** (such as `http://` or `https://`), **host** (location of the server), and **path** (route on the server). In REST APIs, the path often points to a reference entity, like "books".

|   |   |   |
|---|---|---|
|Protocol|Host|Path|
|`https://`|`library-api.postmanlabs.com`|`/books`|

Paths and complete URLs are also sometimes called **API endpoints**.

### Response status codes

The Postman Library API v2 has returned a **[response status code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)** of "**200 OK**". Status codes are indicators of whether a request failed or succeeded.  
  
Status codes have conventions. For example, any status code starting with a "2xx" (a "200-level response") represents a successful call. Get familiar with other status code categories:

|                |              |                                                                                                 |
| -------------- | ------------ | ----------------------------------------------------------------------------------------------- |
| **Code range** | **Meaning**  | **Example**                                                                                     |
| `2xx`          | Success      | `200` - OK  <br>`201` - Created  <br>`204` - No content (silent OK)                             |
| `3xx`          | Redirection  | `301` - Moved (path changed)                                                                    |
| `4xx`          | Client error | `400` - Bad request  <br>`401` - Unauthorized  <br>`403` - Not Permitted  <br>`404` - Not Found |
| `5xx`          | Server error | `500` - Internal server error  <br>`502` - Bad gateway  <br>`504` - Gateway timeout             |
## Query parameters

Remember that the minimum ingredients you need to make a request are:

- a request method (`GET`/`POST`/`PUT`/`PATCH`/`DELETE`, etc)
- a request URL

Some APIs allow you to refine your request further with key-value pairs called **query parameters**. 

### Query parameter syntax

Query parameters are added to the end of the path. They start with a question mark `?`, followed by the key-value pairs in the format: `<key>=<value>`. For example, this request might fetch all photos that have landscape orientation:

`GET https://some-api.com/photos?orientation=landscape`

If there are multiple query parameters, each is separated by an ampersand `&`. Below two query parameters to specify the orientation and size of the photos to be returned:

`GET https://some-api.com/photos?orientation=landscape&size=500x400

### When to use query parameters?

The answer is always: read the API documentation!

Sometimes, query parameters are optional and allow you to add filters or extra data to your responses. Sometimes, they are required in order for the server to process your request. APIs are implemented differently to fulfill different needs. 

The Postman Library API v2 allows you to add optional query parameters on requests to `GET /books` filter the books that come back in response.

## Path Variable

Another way of passing request data to an API is via **path variables** (a.k.a. "path parameters"). A path variable is a dynamic section of a path and is often used for IDs and entity names such as usernames.

### Path Variable syntax

The path variable comes immediately after a slash in the path. For example, the [GitHub API](https://docs.github.com/en/rest/reference/users#get-a-user) allows you to search for GitHub users by providing a username in the path in place of `{username}` below: 

`GET https://api.github.com/users/{username}`

Making this API call with a value for `{username}` will fetch data about that user:

`GET https://api.github.com/users/postmanlabs`

You can have multiple path variables in a single request, such as this endpoint for getting a user's GitHub code repository:

`GET https://api.github.com/repos/{owner}/{repoName}`

For example, to get information about the `newman` code repository from `postmanlabs`:  
  
`GET https://api.github.com/repos/postmanlabs/newman`

### Path vs. query parameters

At first, it is easy to confuse these two parameter types. Let's compare them side by side. 

|   |   |
|---|---|
|**Path Variable**|**Query parameters**|
|ex: `/books/abc123`|ex: `/books?search=borges&checkedOut=false`|
|Located **directly after a slash** in the path. It can **be anywhere on the path**|Located only at the **end of a path**, right after a question mark `?`|
|Accepts **dynamic values**|Accepts **defined query keys** **with potentially dynamic values**.|
|* Often used for IDs or entity names|* Often used for options and filters|

_* These are just conventions! Some APIs might ask you to pass an ID or username in a query parameter like this:_ `/users?username=getpostman`

### Setting and getting collection variables

The `pm` object allows you to set and get collection variables.

To **set** a collection variable, use the `.set()` method with two parameters: the variable name and the variable value

```javascript
pm.collectionVariables.set("variableName", value)
```

  
To **get** a collection variable use the `.get()` method and specify the name of the variable you want to retrieve:

```javascript
pm.collectionVariables.get("variableName")
```

### Local variables

We can also store local variables inside our scripts using JavaScript.

```javascript
// save the "id" value from the response to a variable named "id"
const id = pm.response.json().id
// save the id as a collection variable named "id"
pm.collectionVariables.set("id", id)
```