# Global Params

This section is optional and only used if you would like to describe the HTTP parameters that your service will listen to in a global manner. For example, if you require a security token to ensure every request has been authenticated, or a format variable you would want to take advantage of this feature. As with the variables defined before these are an array of structures with the following keys:

| Variable | Type | Description |
| --- | --- | --- |
| name | string | The name of the HTTP Header |
| description | html or string  | A string or HTML description of your HTTP header. This can be whatever you like. |
| type | string | The type of the HTTP header, usually it could be string, boolean, numeric, binary, etc. |
| required | Boolean | Whether the header is required for any calls or not. The RelaxURL console will use this value if used. |
| default | any | A default value the header is associated with if not passed or sent to the service. |

Here a sample:

```javascrtipt
// Global API Parameters
this.globalParameters = [
    // Sample global parameter, Available keys: name,description,required,default,type
    {name="apikey",description="The apikey needed for request authentication.",required=true},
    {name="format",description="An optional format variable used for content negotiation",required=false, default="json"}
];
```

