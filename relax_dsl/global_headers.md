# Global Headers

This section is optional and only used if you would like to describe the HTTP headers that your service will listen to in a global manner. For example, if you require a X-Auth-Token to ensure every request has been authenticated you would want to take advantage of this feature. As with the variables defined before these are an array of structures with the following keys:

| Variable | Type | Description |
| --- | --- | --- |
| name | string | The name of the HTTP Header |
| description | html or string  | A string or HTML description of your HTTP header. This can be whatever you like. |
| type | string | The type of the HTTP header, usually it could be string, boolean, numeric, binary, etc. |
| required | Boolean | Whether the header is required for any calls or not. The RelaxURL console will use this value if used. |
| default | any | A default value the header is associated with if not passed or sent to the service. |

Here is an sample:

```javascript
// Global API Headers
this.globalHeaders = [
    // Sample global header, Available keys: name,description,required,default,type
    {name="apikey",description="The apikey needed for request authentication.",required=true}
];
```

