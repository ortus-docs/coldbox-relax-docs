# Configuration

The following properties are used to understand your ReSTful service:

| Variable | Type | Description |
| --- | --- | --- |
| title | string | The title for your ReSTful service. Used for documentation purposes |
| description | html or string  | A string or HTML description of your service. This can be whatever you like. |
| entryPoint | URL or struct of URLs  | The main URL entry point for your ReSTful service. e.g. http://api.coldbox.org or if your API service has different URLs or tiers you can make this key be a named structure. |
| extensionDetection  | boolean | A flag that denotes if this ColdBox ReSTful service can detect the format extension via the resource URL. By default ColdBox detects an extension in any resource request. Used for documentation and routes generation. e.g. http://api.coldbox.org/my/resource.json, http://api.coldbox.org/my/resource.xml |
| validExtensions  | list | A list of extensions this ReSTful service can transform to. Used for documentation and routes generation. |
| throwOnInvalidExtension  | boolean | A flag that denotes if the ReSTful service will throw a 406 error when an invalid extension is used or to ignore the error. |


```javascript
// This is where we define our ReSTful service, this is usually
// our first place before even building it, we spec it out.
this.relax = {
    // Service Title
    title = "My ReSTful Service",
    // Service Description
    description = "A very cool ReSTful Service",
    // Service entry point
    entryPoint = "http://www.myapi.com",
    // Does it have extension detection via ColdBox
    extensionDetection = true,
    // Valid format extensions
    validExtensions = "xml,json,jsont,wddx",
    // Does it throw exceptions when invalid extensions are detected
    throwOnInvalidExtension = false     

```

Here is a sample of a multiple entry point service:

```javascript
// This is where we define our ReSTful service, this is usually
// our first place before even building it, we spec it out.
this.relax = {
    // Service Title
    title = "My ReSTful Service",
    // Service Description
    description = "A very cool ReSTful Service",
    // Service entry point
    entryPoint = {
        dev =  "http://dev.myapi.com",
        staging =  "http://stg.myapi.com",
        production =  "http://www.myapi.com"
    },
    // Does it have extension detection via ColdBox
    extensionDetection = true,
    // Valid format extensions
    validExtensions = "xml,json,jsont,wddx",
    // Does it throw exceptions when invalid extensions are detected
    throwOnInvalidExtension = false     
};
```

