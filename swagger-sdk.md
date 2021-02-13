# Swagger SDK

The [ColdBox SwaggerSDK](https://github.com/coldbox-modules/swagger-sdk) is a dependency of the Relax module and is available to allow you to provided consumers of your API with information on paths, methods, expectations and available parameters.

Hypermedia design patterns, usually provided within the content of `OPTIONS` requests to your endpoint, allow you to provide autodiscovery and consumption assistance on-the-fly.

For convenience, built-in methods are available within Relax to simplify the loading and parsing of your existing API documentation.

An example, leveraging an `OPTIONS` request for an endpoint \(and using the conventions of the [Coldbox REST API skeleton](https://github.com/coldbox-templates/rest)\), might look like:

Routing config:

```text
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

Now we add an `options` method to our "Pets" handler to serve the documentation

```text
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

This will serve information on the requested path of the `petstore` API as a JSON response to an `OPTIONS` request \(using the collection example\):

```text
"/pets": {
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
                        "description": "pet response",
                        "schema": {
                            "type": "array",
                            "items": {
                                "type": "object",
                                "allOf": [
                                    {
                                        "type": "object",
                                        "required": [
                                            "name"
                                        ],
                                        "properties": {
                                            "name": {
                                                "type": "string"
                                            },
                                            "tag": {
                                                "type": "string"
                                            }
                                        }
                                    },
                                    {
                                        "required": [
                                            "id"
                                        ],
                                        "properties": {
                                            "id": {
                                                "type": "integer",
                                                "format": "int64"
                                            }
                                        }
                                    }
                                ]
                            }
                        }
                    },
                    "default": {
                        "description": "unexpected error",
                        "schema": {
                            "type": "object",
                            "required": [
                                "code",
                                "message"
                            ],
                            "properties": {
                                "code": {
                                    "type": "integer",
                                    "format": "int32"
                                },
                                "message": {
                                    "type": "string"
                                }
                            }
                        }
                    },
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "x-resourceId": "2243b9a60c66378b60108a67ba948b1c"
            },
            "post": {
                "description": "Creates a new pet in the store.  Duplicates are allowed",
                "operationId": "addPet",
                "parameters": [
                    {
                        "name": "pet",
                        "in": "body",
                        "description": "Pet to add to the store",
                        "required": true,
                        "schema": {
                            "type": "object",
                            "required": [
                                "name"
                            ],
                            "properties": {
                                "name": {
                                    "type": "string"
                                },
                                "tag": {
                                    "type": "string"
                                }
                            }
                        }
                    }
                ],
                "responses": {
                    "200": {
                        "description": "pet response",
                        "schema": {
                            "type": "object",
                            "allOf": [
                                {
                                    "type": "object",
                                    "required": [
                                        "name"
                                    ],
                                    "properties": {
                                        "name": {
                                            "type": "string"
                                        },
                                        "tag": {
                                            "type": "string"
                                        }
                                    }
                                },
                                {
                                    "required": [
                                        "id"
                                    ],
                                    "properties": {
                                        "id": {
                                            "type": "integer",
                                            "format": "int64"
                                        }
                                    }
                                }
                            ]
                        }
                    },
                    "default": {
                        "description": "unexpected error",
                        "schema": {
                            "type": "object",
                            "required": [
                                "code",
                                "message"
                            ],
                            "properties": {
                                "code": {
                                    "type": "integer",
                                    "format": "int32"
                                },
                                "message": {
                                    "type": "string"
                                }
                            }
                        }
                    },
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "x-resourceId": "9b58c599cb38cb1caf7474178e5455df"
            },
            "x-resourceId": "ce256990f68429fe5bbf34dd4676b0be"
}
```

Hypermedia design patterns in your API responses, allow for self-discovery and ease development for API consumption.

