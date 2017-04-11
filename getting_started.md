# Getting Started

Relax comes with three example API's which are configured by default:

* Swagger Petstore - The swagger Petstore API example, which is described using the OpenAPI/Swagger specification
* Forgebox API - Version 2 of the Forgebox API, which is described through the, now-deprecated, RelaxDSL specification. 
* MyAPI - Another example, using the RelaxDSL specification.  

Both `Forgebox` and `MyAPI` may be exported from within the interface in to a normalized Swagger JSON schema, while the `Petstore` example provides and complete example of using a nested file structure to contain different parts of your API documentation.

## Configuration

For custom configuration of your API documentation, you simply add a `relax` configuration to your `Coldbox.cfc` configuration file:

Below is the default configuration structure:

```javascript
// Relax Configuration Settings
relax = {
    // The location of the relaxed APIs, defaults to models.resources
    APILocation = "models/resources",
    // Default API to load, name of the directory inside of resources
    defaultAPI = "forgebox",
    // Whether to cache the API Service as a singleton - In development/authoring, you'll want this set to false
    cache = false
};
```

Note that the `APILocation` key denotes the path to your API resources.  You will need to have at lease one API described, in one of the supported specifications, in order to load a default API. You may import new API documentation from the interface, and create additional API's as you continue to develop new services and endpoints. 

## Considerations

As you develop your API endpoints, you'll find that the size of your API documentation quickly grows with sample requests, responses, and general documentation on parameters and security constraints.   For this reason, it is recommended that you take an "Active Entity" approach to separation of your API documentation.  For example, group together a collections of endpoints and paths which related to specific segments of your API.  Expanding the "Petstore" example, you might have API's for:

* `/pets`
* `/stores`
* `/products`
* `/orders`

By segmenting your documentation in to functional groups, you make updates and addition of endpoints easier, in the long run.


