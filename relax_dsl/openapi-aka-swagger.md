## Open API/Swagger

As of Relax v2.3 and above, the [OpenAPI v2.0](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md) is the default recommended format for documentation in Relax.  The previous RelaxDSL has been deprecated and is schedule to sunset at Relax v4.0.

The OpenAPI specification offers a convenient and portable way to describe your API, its requirements, parameters, and data conventions.   You may also choose to use this to describe your API in the form of [HTTP OPTIONS responses](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) to fulfill [CORS requirements](https://www.w3.org/TR/cors/) or to allow rich [hypermedia](https://en.wikipedia.org/wiki/HATEOAS) documentation for your consumers.

Example \( a segment of the [Forgebox API](https://www.forgebox.io/) \):

```
{
    "swagger": "2.0",
    "info": {
        "contact": {
          "name": "Ortus Solutions",
          "email": "support@ortussolutions.com",
          "url": "http://forgebox.io"
        },
        "termsOfService": "https://www.forgebox.io/policies/terms",
        "version": "2.0",
        "license": {
          "name": "Trademark/Copyright",
          "url": "https://www.forgebox.io/policies/terms"
        },
        "title": "ForgeBox IO",
        "description": "This is the API which powers ForgeBox"
    },
    "host": "forgebox.io",
    "basePath": "/api/v1",,
    "x-entryPoint": {
        "development": "http://localhost:9095",
        "production": "https://forgebox.io",
        "staging": "http://forgebox.stg.ortussolutions.com"
    },
    "schemes": "https",
    "consumes": [
        "application/json",
        "multipart/form-data",
        "application/x-www-form-urlencoded"
    ],
    "produces": [
        "application/json"
    ],
    "paths": {
        "/echo": {
            "x-resourceId": "c2de46855ecc5e676a20e368f4e70297",
            "get": {
                "x-coldbox-handler": "Main",
                "parameters": {
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/json"
                ],
                "x-resourceId": "aeaa242ea76932bd878ddfb1c1f2d881",
                "responses": {
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "Main.echo",
                "description": "Simple API echo command"
            }
        }
    },
    "securityDefinitions": {
        "x-app-token": {
            "in": "header",
            "name": "x-app-token",
            "type": "basic",
            "description": "The secret application token"
        }
    },
    "x-extensionDetection": true,
    "x-throwOnInvalidExtension": false
}
```

Note the use of the `x-` attributes, which allow for extensions of the Swagger specification,  In addition, more complex API's can use the `$ref` syntax to denote locations and keys of relative JSON files:

```
"paths": {
        "/echo": {"$ref": "paths.json#echo"}
},
```

This notates that the definition for the path `/echo` is found in `paths.json` under the `echo` key.  Using the `$ref` notation allows you to store schema examples and other code samples separate from the main JSON or YAML description of your site.

### YAML Support

Per the Swagger formats description:

> The files describing the RESTful API in accordance with the Swagger specification are represented as JSON objects and conform to the JSON standards. YAML, being a superset of JSON, can be used as well to represent a Swagger specification file.

Relax includes support for YAML-format API descriptions, as well.

For full descriptions and examples of the schema specification [read the official OpenAPI v2 specification](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md).

