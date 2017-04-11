# Installation

Use [CommandBox](https://www.gitbook.com/book/ortus/commandbox-documentation/details) to install

`box install relax`

Or, to install the bleeding-edge version

`box install relax@be`

## System Requirements

* Lucee 4.5+
* Railo 4+
* ColdFusion 9+

## Settings

You will need to update the your `ColdBox.cfc` with a `relax` structure with your preferred settings for Relax.

```
// Relax Configuration Settings
relax = {
    // The location of the relaxed APIs, defaults to models.resources
    APILocation = "models.resources",
    // Default API to load, name of the directory inside of resources
    defaultAPI = "forgebox",
    // Whether to cache the API Service as a singleton - In development/authoring, you'll want this set to false
    cache = false
};

```

## Modeling

You can look at the samples inside of the `relax` module under the `models/resources` directory.    
  
You may also open up the Relax ui and click the "Export" button on the sidebar to export an example JSON schema which may be customized and then imported back in to Relax.  
  
For reference, the the contents of that export, at the present, would be:



```
{
    "swagger": "2.0",
    "info": {
        "contact": {},
        "termsOfService": "",
        "version": "",
        "license": {},
        "title": "My RESTFul Service",
        "description": "A very cool RESTFul Service"
    },
    "host": "www.myapi.com",
    "basePath": "/",
    "schemes": "http",
    "consumes": [
        "application/json",
        "multipart/form-data",
        "application/x-www-form-urlencoded"
    ],
    "produces": [
        "application/xml",
        "application/json",
        "application/jsont",
        "application/wddx",
        "text/html"
    ],
    "paths": {
        "/api/users": {
            "put": {
                "x-coldbox-handler": "rest.user",
                "parameters": {
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/xml",
                    "application/json",
                    "application/jsont",
                    "application/wddx",
                    "text/html"
                ],
                "x-resourceId": "423bb48aee1fdd4188d0437fd34b3a37",
                "responses": {
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "rest.user.list",
                "description": "Returns all users"
            },
            "x-resourceId": "5dd78a14d6e453994bd4d5c563f90e04",
            "get": {
                "x-coldbox-handler": "rest.user",
                "parameters": {
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/xml",
                    "application/json",
                    "application/jsont",
                    "application/wddx",
                    "text/html"
                ],
                "x-resourceId": "20bab3eff0b870b1f3138093f84ffc8e",
                "responses": {
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "rest.user.list",
                "description": "Returns all users"
            },
            "post": {
                "x-coldbox-handler": "rest.user",
                "parameters": {
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/xml",
                    "application/json",
                    "application/jsont",
                    "application/wddx",
                    "text/html"
                ],
                "x-resourceId": "5cb14ce2dfbed7be9370e932362111ba",
                "responses": {
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "rest.user.list",
                "description": "Returns all users"
            }
        },
        "/api/myResource": {
            "x-resourceId": "c4c000ce2d6075b2f442c39c5834bbb2",
            "get": {
                "x-coldbox-handler": "rest.myUser",
                "parameters": {
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/xml",
                    "application/json",
                    "application/jsont",
                    "application/wddx",
                    "text/html"
                ],
                "x-resourceId": "b9644301f7e1e557b3f63f1df8f9da50",
                "responses": {
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "rest.myUser",
                "description": "Returns of my available resources"
            },
            "post": {
                "x-coldbox-handler": "rest.myUser",
                "parameters": {
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/xml",
                    "application/json",
                    "application/jsont",
                    "application/wddx",
                    "text/html"
                ],
                "x-resourceId": "752d1e616a6d0dfa1524d4fd827ebf19",
                "responses": {
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "rest.myUser",
                "description": "Returns of my available resources"
            }
        },
        "/api/user/{username}": {
            "put": {
                "x-coldbox-handler": "rest.user",
                "parameters": {
                    "username": {
                        "required": true,
                        "in": "path",
                        "type": "string",
                        "x-defaultValue": "",
                        "description": "The resource username to interact with"
                    },
                    "firstName": {
                        "required": true,
                        "in": "formData",
                        "type": "string",
                        "description": "The user firstname. Only used on PUT and POST operations"
                    },
                    "lastName": {
                        "required": true,
                        "in": "formData",
                        "type": "string",
                        "description": "The user lastname. Only used on PUT and POST operations"
                    },
                    "email": {
                        "required": false,
                        "in": "formData",
                        "type": "string",
                        "description": "The user email. Only used on PUT and POST operations"
                    },
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/xml",
                    "application/json",
                    "application/jsont",
                    "application/wddx",
                    "text/html"
                ],
                "x-resourceId": "20a39f01ddab3c47ae9b61a87bb3eaef",
                "responses": {
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "rest.user.{'get':'view','post':'create','put':'update','delete','remove'}",
                "description": "The representation for system users.  You can also interact with creation, updating and deletion via this resource"
            },
            "x-resourceId": "2163611f9de439f64b77aededadcd326",
            "get": {
                "x-coldbox-handler": "rest.user",
                "parameters": {
                    "username": {
                        "required": true,
                        "in": "path",
                        "type": "string",
                        "x-defaultValue": "",
                        "description": "The resource username to interact with"
                    },
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/xml",
                    "application/json",
                    "application/jsont",
                    "application/wddx",
                    "text/html"
                ],
                "x-resourceId": "41a531c92e771514f7f3ae973a50ade7",
                "responses": {
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "rest.user.{'get':'view','post':'create','put':'update','delete','remove'}",
                "description": "The representation for system users.  You can also interact with creation, updating and deletion via this resource"
            },
            "delete": {
                "x-coldbox-handler": "rest.user",
                "parameters": {
                    "username": {
                        "required": true,
                        "in": "path",
                        "type": "string",
                        "x-defaultValue": "",
                        "description": "The resource username to interact with"
                    },
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/xml",
                    "application/json",
                    "application/jsont",
                    "application/wddx",
                    "text/html"
                ],
                "x-resourceId": "b72f4b14a1c422c589e14b5400f1829b",
                "responses": {
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "rest.user.{'get':'view','post':'create','put':'update','delete','remove'}",
                "description": "The representation for system users.  You can also interact with creation, updating and deletion via this resource"
            },
            "post": {
                "x-coldbox-handler": "rest.user",
                "parameters": {
                    "username": {
                        "required": true,
                        "in": "path",
                        "type": "string",
                        "x-defaultValue": "",
                        "description": "The resource username to interact with"
                    },
                    "firstName": {
                        "required": true,
                        "in": "formData",
                        "type": "string",
                        "description": "The user firstname. Only used on PUT and POST operations"
                    },
                    "lastName": {
                        "required": true,
                        "in": "formData",
                        "type": "string",
                        "description": "The user lastname. Only used on PUT and POST operations"
                    },
                    "email": {
                        "required": false,
                        "in": "formData",
                        "type": "string",
                        "description": "The user email. Only used on PUT and POST operations"
                    },
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/xml",
                    "application/json",
                    "application/jsont",
                    "application/wddx",
                    "text/html"
                ],
                "x-resourceId": "89a4cede37f15fbd5ff1bbbaec48eb3e",
                "responses": {
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "rest.user.{'get':'view','post':'create','put':'update','delete','remove'}",
                "description": "The representation for system users.  You can also interact with creation, updating and deletion via this resource"
            }
        },
        "/api/tables/{action}": {
            "x-resourceId": "170810066fc87804d4a6a08dba26fc95",
            "get": {
                "x-coldbox-handler": "rest.table",
                "parameters": {
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/xml",
                    "application/json",
                    "application/jsont",
                    "application/wddx",
                    "text/html"
                ],
                "x-resourceId": "96148eae1c77b5237b9344ddee6dc7c0",
                "responses": {
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "rest.table",
                "description": "Returns table actions"
            }
        },
        "/api/user": {
            "x-resourceId": "d2425574595d4e326a17a88cef917034",
            "get": {
                "x-coldbox-handler": "rest.user",
                "parameters": {
                    "userID": {
                        "required": false,
                        "in": "query",
                        "type": "string",
                        "description": "The userID of the User record."
                    },
                    "username": {
                        "required": false,
                        "in": "query",
                        "type": "string",
                        "description": "The username of the User record."
                    },
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/xml",
                    "application/json",
                    "application/jsont",
                    "application/wddx",
                    "text/html"
                ],
                "x-request-samples": {
                    "examples": {
                        "application/json": {
                            "status": "success",
                            "message": "",
                            "data": {
                                "userid": 1001,
                                "username": "admin",
                                "useremail": "admin@server.com",
                                "userfirstname": "Administrator",
                                "userlastname": "",
                                "userrole": "admin",
                                "clientid": 1001,
                                "clientname": "System"
                            }
                        },
                        "default": {
                            "status": "failure",
                            "message": "Error message",
                            "data": ""
                        }
                    },
                    "sample": {
                        "type": "object"
                    },
                    "x-resourceId": "a23757049c02dff3d4efac828e41edc7",
                    "description": "The basic user information will be returned in a flat object."
                },
                "x-resourceId": "f2345b19ba7c3b061c490ba2e42c7330",
                "responses": {
                    "200": {
                        "examples": {
                            "application/json": {
                                "description": "Response for /users/user resource.",
                                "type": "object",
                                "properties": {
                                    "status": {
                                        "type": "string"
                                    },
                                    "message": {
                                        "type": "string"
                                    },
                                    "data": {
                                        "type": "object",
                                        "properties": {
                                            "userid": {
                                                "type": "integer"
                                            },
                                            "username": {
                                                "type": "string"
                                            },
                                            "useremail": {
                                                "type": "string"
                                            },
                                            "userfirstname": {
                                                "type": "string"
                                            },
                                            "userlastname": {
                                                "type": "string"
                                            },
                                            "userrole": {
                                                "type": "string"
                                            },
                                            "clientid": {
                                                "type": "integer"
                                            },
                                            "clientname": {
                                                "type": "string"
                                            }
                                        }
                                    }
                                }
                            },
                            "application/xml": "<?xml version=\"1.0\" encoding=\"utf-8\"?>\n<xs:schema xmlns:xs=\"http://www.w3.org/2001/XMLSchema\" elementFormDefault=\"qualified\">\n\n\t<xs:element name=\"struct\">\n\t\t<xs:complexType>\n\t\t\t<xs:all>\n\t\t\t\t<xs:element name=\"message\" type=\"xs:string\"></xs:element>\n\t\t\t\t<xs:element name=\"status\" type=\"xs:string\"></xs:element>\n\t\t\t\t<xs:element name=\"data\">\n\t\t\t\t\t<xs:complexType>\n\t\t\t\t\t\t<xs:sequence>\n\t\t\t\t\t\t\t<xs:element name=\"struct\">\n\t\t\t\t\t\t\t\t<xs:complexType>\n\t\t\t\t\t\t\t\t\t<xs:all>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userid\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"username\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"useremail\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userlastname\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userfirstname\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userrole\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userstatus\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"clientid\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"clientname\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t</xs:all>\n\t\t\t\t\t\t\t\t</xs:complexType>\n\t\t\t\t\t\t\t</xs:element>\n\t\t\t\t\t\t</xs:sequence>\n\t\t\t\t\t</xs:complexType>\n\t\t\t\t</xs:element>\n\t\t\t</xs:all>\n\t\t</xs:complexType>\n\t</xs:element>\n\n</xs:schema>\n"
                        },
                        "schema": {
                            "type": "object"
                        },
                        "description": "The following will be returned when the format requested is JSON."
                    },
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "rest.user",
                "description": "User resource."
            },
            "post": {
                "x-coldbox-handler": "rest.user",
                "parameters": {
                    "userID": {
                        "required": false,
                        "in": "formData",
                        "type": "string",
                        "description": "The userID of the User record."
                    },
                    "username": {
                        "required": false,
                        "in": "formData",
                        "type": "string",
                        "description": "The username of the User record."
                    },
                    "x-resourceId": "166e64f6c3677d0c513901242a3e702d"
                },
                "produces": [
                    "application/xml",
                    "application/json",
                    "application/jsont",
                    "application/wddx",
                    "text/html"
                ],
                "x-request-samples": {
                    "examples": {
                        "application/json": {
                            "status": "success",
                            "message": "",
                            "data": {
                                "userid": 1001,
                                "username": "admin",
                                "useremail": "admin@server.com",
                                "userfirstname": "Administrator",
                                "userlastname": "",
                                "userrole": "admin",
                                "clientid": 1001,
                                "clientname": "System"
                            }
                        },
                        "default": {
                            "status": "failure",
                            "message": "Error message",
                            "data": ""
                        }
                    },
                    "sample": {
                        "type": "object"
                    },
                    "x-resourceId": "a23757049c02dff3d4efac828e41edc7",
                    "description": "The basic user information will be returned in a flat object."
                },
                "x-resourceId": "e1b3f5bec92ad2667234472c246f780c",
                "responses": {
                    "201": {
                        "examples": {
                            "application/json": {
                                "description": "Response for /users/user resource.",
                                "type": "object",
                                "properties": {
                                    "status": {
                                        "type": "string"
                                    },
                                    "message": {
                                        "type": "string"
                                    },
                                    "data": {
                                        "type": "object",
                                        "properties": {
                                            "userid": {
                                                "type": "integer"
                                            },
                                            "username": {
                                                "type": "string"
                                            },
                                            "useremail": {
                                                "type": "string"
                                            },
                                            "userfirstname": {
                                                "type": "string"
                                            },
                                            "userlastname": {
                                                "type": "string"
                                            },
                                            "userrole": {
                                                "type": "string"
                                            },
                                            "clientid": {
                                                "type": "integer"
                                            },
                                            "clientname": {
                                                "type": "string"
                                            }
                                        }
                                    }
                                }
                            },
                            "application/xml": "<?xml version=\"1.0\" encoding=\"utf-8\"?>\n<xs:schema xmlns:xs=\"http://www.w3.org/2001/XMLSchema\" elementFormDefault=\"qualified\">\n\n\t<xs:element name=\"struct\">\n\t\t<xs:complexType>\n\t\t\t<xs:all>\n\t\t\t\t<xs:element name=\"message\" type=\"xs:string\"></xs:element>\n\t\t\t\t<xs:element name=\"status\" type=\"xs:string\"></xs:element>\n\t\t\t\t<xs:element name=\"data\">\n\t\t\t\t\t<xs:complexType>\n\t\t\t\t\t\t<xs:sequence>\n\t\t\t\t\t\t\t<xs:element name=\"struct\">\n\t\t\t\t\t\t\t\t<xs:complexType>\n\t\t\t\t\t\t\t\t\t<xs:all>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userid\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"username\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"useremail\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userlastname\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userfirstname\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userrole\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userstatus\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"clientid\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"clientname\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t</xs:all>\n\t\t\t\t\t\t\t\t</xs:complexType>\n\t\t\t\t\t\t\t</xs:element>\n\t\t\t\t\t\t</xs:sequence>\n\t\t\t\t\t</xs:complexType>\n\t\t\t\t</xs:element>\n\t\t\t</xs:all>\n\t\t</xs:complexType>\n\t</xs:element>\n\n</xs:schema>\n"
                        },
                        "schema": {
                            "type": "object"
                        },
                        "description": "The following will be returned when the format requested is JSON."
                    },
                    "default": {
                        "examples": {
                            "application/xml": "<?xml version=\"1.0\" encoding=\"utf-8\"?>\n<xs:schema xmlns:xs=\"http://www.w3.org/2001/XMLSchema\" elementFormDefault=\"qualified\">\n\n\t<xs:element name=\"struct\">\n\t\t<xs:complexType>\n\t\t\t<xs:all>\n\t\t\t\t<xs:element name=\"message\" type=\"xs:string\"></xs:element>\n\t\t\t\t<xs:element name=\"status\" type=\"xs:string\"></xs:element>\n\t\t\t\t<xs:element name=\"data\">\n\t\t\t\t\t<xs:complexType>\n\t\t\t\t\t\t<xs:sequence>\n\t\t\t\t\t\t\t<xs:element name=\"struct\">\n\t\t\t\t\t\t\t\t<xs:complexType>\n\t\t\t\t\t\t\t\t\t<xs:all>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userid\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"username\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"useremail\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userlastname\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userfirstname\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userrole\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"userstatus\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"clientid\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t\t<xs:element name=\"clientname\" type=\"xs:string\"></xs:element>\n\t\t\t\t\t\t\t\t\t</xs:all>\n\t\t\t\t\t\t\t\t</xs:complexType>\n\t\t\t\t\t\t\t</xs:element>\n\t\t\t\t\t\t</xs:sequence>\n\t\t\t\t\t</xs:complexType>\n\t\t\t\t</xs:element>\n\t\t\t</xs:all>\n\t\t</xs:complexType>\n\t</xs:element>\n\n</xs:schema>\n"
                        },
                        "schema": {
                            "type": "object"
                        },
                        "description": "The following will be returned when the format requested is XML."
                    },
                    "x-resourceId": "a9f0a3a63fe6b5bd954760c6ac09e85c"
                },
                "operationId": "rest.user",
                "description": "User resource."
            }
        }
    },
    "securityDefinitions": {
        "apikey": {
            "in": "header",
            "name": "apikey",
            "type": "basic",
            "description": "The apikey needed for request authentication."
        }
    },
    "x-extensionDetection": true,
    "x-throwOnInvalidExtension": false,
    "x-entryPoint": {
        "DEV": "http://dev.myapi.com",
        "PRODUCTION": "http://www.myapi.com"
    }
}

```



