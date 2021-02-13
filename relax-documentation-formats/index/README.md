# Relax Programmatic DSL \(Deprecated\)

## Relax Programmatic DSL

Deprecated as of Relax 2.3, but still available, the Relax DSL configuration object which is mixed into a simple Relax CFC Definition Object so you can use all the methods in this CFC to define RESTful web services. All functions can be concatenated to create a programmatic DSL. This DSL is exportable to OpenAPI formats.

#### Example Using the Forgebox API:

```text
this.relax = {
    // Service Title
    title = "ForgeBox IO",
    // Service Description
    description = "This API powers ForgeBox",
    // Service entry point, can be a single string or name value pairs to denote tiers
    //entryPoint = "http://www.myapi.com",
    entryPoint = {
        "production"     : "https://forgebox.io/api/v1",
        "staging"     : "http://forgebox.stg.ortussolutions.com/api/v1",
        "development"     : "http://localhost:9095/api/v1"
    },
    // Does it have extension detection via ColdBox
    extensionDetection = true,
    // Valid format extensions
    validExtensions = "json",
    // Does it throw exceptions when invalid extensions are detected
    throwOnInvalidExtension = false        
};

/************************************** GLOBAL PARAMS +  HEADERS *********************************************/

// Global API Headers
globalHeader( name="x-app-token", description="The secret application token", required=true, type="string" );

/************************************** RESOURCES *********************************************/

// ECHO
resource( pattern="/echo", handler="Main", action="echo" )
    .description( "Simple API echo command" )
    .defaultFormat( "json" )
    .methods( "GET" );
```

## Configuration

The relaxed service information. From here you will define the RESTful service endpoints, extension detection, valid formats, and more.

### Arguments

| Argument | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| title | any | Yes | --- | The title of the RESTful service |
| description | any | Yes | --- | The description of the RESTful service |
| entryPoint | any | Yes | --- | A simple URL or a structure of entry points |
| extensionDetection | any | No | true | Will this API do extension detection |
| validExtensions | any | No | json,jsont,xml,html,htm,rss | The valid extensions to detect |
| The valid extensions to detec | any | No | false | Throw on invalid extensions or not |

## Global Headers

Add a global header to the relax definition

### Arguments

| Argument | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| name | any | Yes | --- | The name of the header |
| description | any | No |  | The description of the header |
| required | any | No | false | Is the header required or not |
| default | any | No |  | The default value of this header |
| type | any | No | string | The type of the incoming header |

## Global Params

Add a global parameter to the relax definition

### Arguments

| Argument | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| name | any | Yes | --- | The name of the parameter |
| description | any | No |  | The description of the parameter |
| required | any | No | false | Is the parameter required or not |
| default | any | No |  | The default value of this parameter |
| type | any | No | string | The type of the incoming parameter |

