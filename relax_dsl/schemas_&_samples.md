# Schemas & Samples

You can define samples and schemas for your resources by using the response structure by using the schemas and samples keys, which in turn are array of definitions.

```javascript
response={Schem
    schemas=[
        {format="json", description="The following will be returned when the format requested is JSON.", body=fileRead("#dirPath#schemas/user/user.json") },
        {format="xml", description="The following will be returned when the format requested is XML.", body=fileRead("#dirPath#schemas/user/user.xsd") }
    ],
    samples=[
        {format="json", description="The basic user information will be returned in a flat object.", body=fileRead("#dirPath#samples/user/user.json")},
        {format="json", description="If the requested user is not found, or some other error has occurred, the resopnse will be like the following.", body=fileRead("#dirPath#samples/user/failure.json")}
    ]
}
```

As you can see, you can define multiple declarations for each category. Each containing:

| Variable | Type | Description |
| --- | --- | --- |
| format | string | The format of the schema or sample |
| description | string | The description of the schema or sample |
| action | string  | The contents of the schema or sample, usually in the specified format like JSON or XML. |



