# Resources

Add a new resource to the API definition, you can then concatenate more methods to the same resource: _methods\(\),description\(\),header\(\),parameter\(\),placeholder\(\),schema\(\),sample\(\)_

## Arguments

| Argument | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| pattern | any | Yes | --- | The SES pattern to register for the resource |
| handler | any | No | --- | The description of the parameter |
| action | any | No | --- | Is the parameter required or not |

## Default Format

Define a default return format for a resource

### Arguments

| Argument | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| format | any | Yes | --- | The format that will be the default |

## Description

Add a description to a resource

### Arguments

| Argument | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| description | any | Yes | --- | The description |

## Methods

Add methods to a resource

### Arguments

| Argument | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| methods | any | Yes | --- | The methods list to allow |

## Default Method

Define a default HTTP method for a resource

## Arguments

| Argument | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| method | any | Yes | --- | The HTTP method that will be the default |

