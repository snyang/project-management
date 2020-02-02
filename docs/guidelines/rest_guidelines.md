# Guidelines for RESTful Interface

## Introduction
This is a guidelines for RESTful applications.

## Method

[Using HTTP Methods for RESTful Services]

| Method | Meaning            |
| ------ | ------------------ |
| POST   | Create             |
| GET    | Read               |
| PUT    | Update/Replace     |
| DELETE | Delete             |

## Exceptions and Error Codes
- Code: 200 - OK
For good return.

- Code: 401 - Unauthorized
If the user is not login or session expired.

- Code: 402 - Payment Required
For payment operations if the user has not paid it.

- Code: 403 - Forbidden
Use it when the user does not have permission to run the operation.

- Code: 404 - Not Found
For get method, when the specific resource is not found.

- Code: 409 - Conflict if the resource already exists
For create operation, when there is a conflict for unique keys.

- Code: 500 - Internal Exception
For normal exceptions

- Code: 501 - Not Implemented
For not implemented operations.

## URL
- Get a resource with id
GET resources/{id}

- Get a resource with name
GET resources?name=Name

- Create a resource
POST resources
body with creating resource content
response body with created resource content.

- Update a resource
PUT resources/{id}
body with updating resource content

- Update a resource with specific field value
PUT resources/{id}?name=Name

- Delete a resource
DELETE resources/{id}

- Filter resources with simple conditions
GET resources?name=Name
GET resources?gender=woman&orderby=Name

- Search resources with complex conditions
There are 2 approaches, one is using GET and another one is using POST.
  - GET with a complex URL
    _Pure RESTful methodism like it._
  GET resources?filter=[(field,operation,value),(name, like, A)]

  - POST with body
  POST resources/search
  body with search options

- Action
  - Prefer to consider the action as a update first.
  PUT resources/{id}?islocked=true
  
  - Use action parameter
  PUT resources/{id}?action=lock&param=value&...
  PUT resources?action=lock&param=value&...

  - Define the action like a resource.
  _Pure RESTful methodism does not like the method, as it is not a resource._
  PUT resources/{id}/actions/lock?param=value&...
  PUT resources/actions/lock?id={id}&param=value&...
  PUT resources/!/actions/lock?id={id}&param=value&...

## Body
- Use json as the body format.

## Response Content
- Use json as the content format.

## References
