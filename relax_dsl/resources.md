# Resources

The following section is essential as it describes the ReSTful resources you will expose through your service. Please remember that order is important as it will be used to generate the ColdBox routes file, which in turn are your ReSTful routes. We will create a array of structures with the following keys for each resource:

| Variable | Type | Description |
| --- | --- | --- |
| pattern | string | The ColdBox route pattern to define, you can use ALL the same parameters you do in a ColdBox URL Mapping route. |
| handler | string | The event notation for the package+event to redirect this request to. This key is optional as the handler can be embedded also in the pattern as :handler. |
| action | string or JSON or Implicit Struct  | The normal action or ReSTful action (json) to redirect this request to. This key is optional as the action can be embedded also in the pattern as :action or left blank to default it to index. ReSTful routing can also be used, which is what we recommend, by making this entry a JSON structure: e.g. action="{'get':'list', 'post':'create', 'delete':'remove'}" |
| description | HTML or string  | A description about the resource you are exposing. Try to be descriptive, use HTML or make it pretty. |
| methods | list | A list of allowed HTTP methods this resource can listen to. |
| defaultMethod  | string | The default method this resource responds to. By default it is set to GET. |
| defaultFormat  | string | The default format this resource responds to. By default format is empty. |
| headers | array of headers  | AAn array of structures where you define HTTP headers this resource can listen to. The header structure to use is the same as the global headers described before: name, description, type, required and default. |
| parameters | array of parameters  | AAn array of structures where you define HTTP URL/FORM parameters this resource can listen to. The structure to use is the same as the global headers described before: name, description, type, required and default. |
| placeholders | array of placeholders  | AAn array of structures where you describe the pattern placeholders (:placeholder). These placeholders get translated by ColdBox URL mappings into request collection variables, so you can use this array to define them for documentation purposes. The structure to use is the same as the global headers described before: name, description, type, required and default. |
| response | structure | A structure that can hold two keys: schemas and samples for defining them for the resource. |

Here is a sample:

```javascript
// Define our Relaxed ReSTful resources in order just like you are defining routes
// Each header, parameter or placeholder is a structure with the following keys:
// {name="",type="",required="",default="",description=""}
this.resources = [
    {pattern="/api/users",handler="rest.user",action="list", defaultMethod="GET", defaultFormat="json"
     description="Returns all users",
     methods="GET",headers=[],parameters=[],placeholders=[]},
     
     {pattern="/api/user/:username",handler="rest.user",action="{'get':'view','post':'create','put':'update','delete','remove'}",
      description="The representation for system users.  You can also interact with creation, updating and deletion via this resource",
      methods="GET,POST,PUT,DELETE",
      headers=[],
      parameters=[
        {name="firstName",description="The user firstname. Only used on PUT and POST operations",required="false"},
        {name="lastName",description="The user lastname. Only used on PUT and POST operations",required="false"},
        {name="email",description="The user email. Only used on PUT and POST operations",required="false"}
      ],
      placeholders=[{name="username",description="The resource username to interact with",required=true}]}
];
```

That's it! Once your DSL is defined, you can start up your relax module and get cooking with it. Here are some screenshots and videos about Relax.

