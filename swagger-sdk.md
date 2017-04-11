## Swagger SDK - Leverage Hypermedia Discovery in your RESTful Services

The ColdBox SwaggerSDK is a dependency of the Relax module and is available to allow you to provided consumers of your API with information on paths, methods, expectations and available parameters.

Hypermedia design patterns, usually provided within the content of `OPTIONS` requests to your endpoint, allow you to provide autodiscovery and consumption assistance on-the-fly.

For convenience, built-in methods are available within Relax to simplify the loading and parsing of your existing API documentation.

An example, leveraging an `OPTIONS` request for an endpoint (and using the Base REST handler), might look like:


Routing config:

```
//Pet Routes - collections and additions
addRoute(
	pattern = "api/pets",
	handler = "Pets",
	action  = {
		"GET"    : "index",
		"POST"   : "create",
		"PUT"    : "onInvalidHTTPMethod",
		"PATCH"  : "onInvalidHTTPMethod",
		"DELETE" : "delete",
		"OPTIONS": "options"
	}
);

//Pet Routes - entity methods
addRoute(
	pattern = "api/pets/:id",
	handler = "Pets",
	action  = {
		"GET"    : "get",
		"POST"   : "onInvalidHTTPMethod",
		"PUT"    : "update",
		"PATCH"  : "update",
		"DELETE" : "delete",
		"OPTIONS": "options"
	}
);
```


Now we add an `options` method to our handler to serve the documentation

```
public function options( event, rc, prc ){
    
    petOptions = getInstance( "APIService@relax" ).loadAPI( 'petstore' );
    if( structKeyExists( rc, "id" )){
    	prc.response.setData( petOptions.paths[ "/pets/{id}" ] );
    } else {
	prc.response.setData( petOptions.paths[ "/pets" ] );
    }
    prc.response.setStatusCode( STATUS.SUCCESS );

}
```

This will serve information on the requested path of the `petstore` API as a JSON response to an `OPTIONS` request (using the collection example):


```
{
    "get": {
      "description": "Returns all pets from the system that the user has access to\nNam sed condimentum est. Maecenas tempor sagittis sapien, nec rhoncus sem sagittis sit amet. Aenean at gravida augue, ac iaculis sem. Curabitur odio lorem, ornare eget elementum nec, cursus id lectus. Duis mi turpis, pulvinar ac eros ac, tincidunt varius justo. In hac habitasse platea dictumst. Integer at adipiscing ante, a sagittis ligula. Aenean pharetra tempor ante molestie imperdiet. Vivamus id aliquam diam. Cras quis velit non tortor eleifend sagittis. Praesent at enim pharetra urna volutpat venenatis eget eget mauris. In eleifend fermentum facilisis. Praesent enim enim, gravida ac sodales sed, placerat id erat. Suspendisse lacus dolor, consectetur non augue vel, vehicula interdum libero. Morbi euismod sagittis libero sed lacinia.\n\nSed tempus felis lobortis leo pulvinar rutrum. Nam mattis velit nisl, eu condimentum ligula luctus nec. Phasellus semper velit eget aliquet faucibus. In a mattis elit. Phasellus vel urna viverra, condimentum lorem id, rhoncus nibh. Ut pellentesque posuere elementum. Sed a varius odio. Morbi rhoncus ligula libero, vel eleifend nunc tristique vitae. Fusce et sem dui. Aenean nec scelerisque tortor. Fusce malesuada accumsan magna vel tempus. Quisque mollis felis eu dolor tristique, sit amet auctor felis gravida. Sed libero lorem, molestie sed nisl in, accumsan tempor nisi. Fusce sollicitudin massa ut lacinia mattis. Sed vel eleifend lorem. Pellentesque vitae felis pretium, pulvinar elit eu, euismod sapien.\n",
      "operationId": "findPets",
      "parameters": [
        {
          "name": "tags",
          "in": "query",
          "description": "tags to filter by",
          "required": false,
          "type": "array",
          "collectionFormat": "csv",
          "items": {
            "type": "string"
          }
        },
        {
          "name": "limit",
          "in": "query",
          "description": "maximum number of results to return",
          "required": false,
          "type": "integer",
          "format": "int32"
        }
      ],
      "responses": {
        "200": {
          "description": "pets collection response",
          "schema": {
            "type": "array",
            "items": {
              "$ref": "definitions/Pet.json"
            }
          }
        },
        "default": {
          "description": "unexpected error",
          "schema": {
            "$ref": "definitions/Error.json"
          }
        }
      }
}
```

Hypermedia design patterns in your API responses, allow for self-discovery and ease development for API consumption.



