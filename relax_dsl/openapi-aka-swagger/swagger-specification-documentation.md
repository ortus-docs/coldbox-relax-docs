For convienience, additional documentation on th

### Data Types

Primitive data types in the Swagger Specification are based on the types supported by the[JSON-Schema Draft 4](https://tools.ietf.org/html/draft-zyp-json-schema-04#section-3.5). Models are described using the[Schema Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#schemaObject)which is a subset of JSON Schema Draft 4.

An additional primitive data type`"file"`is used by the[Parameter Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#parameterObject)and the[Response Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#responseObject)to set the parameter type or the response as being a file.

Primitives have an optional modifier property`format`. Swagger uses several known formats to more finely define the data type being used. However, the`format`property is an open`string`-valued property, and can have any value to support documentation needs. Formats such as`"email"`,`"uuid"`, etc., can be used even though they are not defined by this specification. Types that are not accompanied by a`format`property follow their definition from the JSON Schema \(except for`file`type which is defined above\). The formats defined by the Swagger Specification are:

| Common Name | [`type`](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#dataTypeType) | [`format`](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#dataTypeFormat) | Comments |
| :--- | :--- | :--- | :--- |
| integer | `integer` | `int32` | signed 32 bits |
| long | `integer` | `int64` | signed 64 bits |
| float | `number` | `float` |  |
| double | `number` | `double` |  |
| string | `string` |  |  |
| byte | `string` | `byte` | base64 encoded characters |
| binary | `string` | `binary` | any sequence of octets |
| boolean | `boolean` |  |  |
| date | `string` | `date` | As defined by`full-date`-[RFC3339](http://xml2rfc.ietf.org/public/rfc/html/rfc3339.html#anchor14) |
| dateTime | `string` | `date-time` | As defined by`date-time`-[RFC3339](http://xml2rfc.ietf.org/public/rfc/html/rfc3339.html#anchor14) |
| password | `string` | `password` | Used to hint UIs the input needs to be obscured. |

### Schema

#### Swagger Object

This is the root document object for the API specification. It combines what previously was the Resource Listing and API Declaration \(version 1.2 and earlier\) together into one document.

##### Fixed Fields

| Field Name | Type | Description |
| :--- | :--- | :--- |
| swagger | `string` | **Required.**Specifies the Swagger Specification version being used. It can be used by the Swagger UI and other clients to interpret the API listing. The value MUST be`"2.0"`. |
| info | [Info Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#infoObject) | **Required.**Provides metadata about the API. The metadata can be used by the clients if needed. |
| host | `string` | The host \(name or ip\) serving the API. This MUST be the host only and does not include the scheme nor sub-paths. It MAY include a port. If the`host`is not included, the host serving the documentation is to be used \(including the port\). The`host`does not support[path templating](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#pathTemplating). |
| basePath | `string` | The base path on which the API is served, which is relative to the[`host`](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#swaggerHost). If it is not included, the API is served directly under the`host`. The value MUST start with a leading slash \(`/`\). The`basePath`does not support[path templating](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#pathTemplating). |
| schemes | \[`string`\] | The transfer protocol of the API. Values MUST be from the list:`"http"`,`"https"`,`"ws"`,`"wss"`. If the`schemes`is not included, the default scheme to be used is the one used to access the Swagger definition itself. |
| consumes | \[`string`\] | A list of MIME types the APIs can consume. This is global to all APIs but can be overridden on specific API calls. Value MUST be as described under[Mime Types](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#mimeTypes). |
| produces | \[`string`\] | A list of MIME types the APIs can produce. This is global to all APIs but can be overridden on specific API calls. Value MUST be as described under[Mime Types](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#mimeTypes). |
| paths | [Paths Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#pathsObject) | **Required.**The available paths and operations for the API. |
| definitions | [Definitions Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#definitionsObject) | An object to hold data types produced and consumed by operations. |
| parameters | [Parameters Definitions Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#parametersDefinitionsObject) | An object to hold parameters that can be used across operations. This property_does not_define global parameters for all operations. |
| responses | [Responses Definitions Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#responsesDefinitionsObject) | An object to hold responses that can be used across operations. This property_does not_define global responses for all operations. |
| securityDefinitions | [Security Definitions Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#securityDefinitionsObject) | Security scheme definitions that can be used across the specification. |
| security | \[[Security Requirement Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#securityRequirementObject)\] | A declaration of which security schemes are applied for the API as a whole. The list of values describes alternative security schemes that can be used \(that is, there is a logical OR between the security requirements\). Individual operations can override this definition. |
| tags | \[[Tag Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#tagObject)\] | A list of tags used by the specification with additional metadata. The order of the tags can be used to reflect on their order by the parsing tools. Not all tags that are used by the[Operation Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operationObject)must be declared. The tags that are not declared may be organized randomly or based on the tools' logic. Each tag name in the list MUST be unique. |
| externalDocs | [External Documentation Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#externalDocumentationObject) | Additional external documentation. |

##### Patterned Objects

| Field Pattern | Type | Description |
| :--- | :--- | :--- |
| ^x- | Any | Allows extensions to the Swagger Schema. The field name MUST begin with`x-`, for example,`x-internal-id`. The value can be`null`, a primitive, an array or an object. See[Vendor Extensions](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#vendorExtensions)for further details. |

#### 

  
  


