# Relax DSL

Once you have configured the Relax module setup and ready for operation you can start by defining your RESTful service. You will do this by creating a Simple CFC–usually in the root of the resource folder, for simplicity–named Relax.cfc or Relax.json. In this component or JSON file, you will create several public variables (using the this scope) that will define your service's parameters, headers, resources and so much more. You can also use our programmatic DSL, which is much cleaner than implicit data structures. This CFC will represent your RESTful service and ColdBox Relax will generate documentation from it, create testable URLs for you and it is a great way for you to model your service. Please note that if you use JSON for defining your service, it must validate according to the same structure elements you will see here. http://www.jsonlint.com is a great way for you to format and validate your JSON representations.

> **IMPORTANT** The implicit data structure definitions could be deprecated in future versions in favor of the programmatic DSL. 

| Variable | Type | Description |
| --- | --- | --- |
| relax | struct | The structure used to define the ReSTful service |
| globalHeaders  | array of structs  | Where you define global headers your ReSTful service expects |
| globalParameters  | array of structs  | Where you define global parameters your ReSTful service expects |
| resources  | array of structs  | Where you define your ReSTful resource patterns. |

```javascript
component{

    // relax dsl
    this.relax = {};
    
    // Global Headers
    this.globalHeaders = [];
    
    // Global Parameteres
    this.globalParameters = [];
    
    // Resources
    this.resources = [];
}
```



