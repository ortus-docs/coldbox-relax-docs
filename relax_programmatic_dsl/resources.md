# Resources

Add a new resource to the API definition, you can then concatenate more methods to the same resource: *methods(),description(),header(),parameter(),placeholder(),schema(),sample()*

## Arguments

| Argument | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| pattern | any | Yes | --- | The SES pattern to register for the resource |
| handler | any | No | --- | The description of the parameter |
| action | any | No | --- | Is the parameter required or not |


## Default Format

Define a default return format for a resource

###Arguments

| Argument | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| format | any | Yes | --- | The format that will be the default |

## Description

Add a description to a resource

###Arguments

| Argument | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| description | any | Yes | --- | The description |

## Methods

Add methods to a resource

###Arguments

| Argument | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| methods | any | Yes | --- | The methods list to allow |

## Default Method

Define a default HTTP method for a resource

## Arguments

| Argument | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| method | any | Yes | --- | The HTTP method that will be the default |

# Set All Params

Set all the required parameters of a resource

###Arguments

| Argument | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| params | array | Yes | --- | Set the parameters of a resource |

# Placeholders
Add a placeholder to a resource

## Arguments

| Argument | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| name | any | Yes | --- | The name of the placeholder |
| description | any | No |  | The description of the placeholder |
| required | any | No | false | Is the placeholder required |
| default | any | No |  | The default value of the placeholder |
| type | any | No | string | The type of the placeholder |

## Set All Placeholders
Set all the required placeholders of a resource

### Arguments

| Argument | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| placeholders | array | Yes | --- | Set the placeholders of a resource |


## Headers

Add a header to a resource

###Arguments

| Argument | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| name | any | Yes | --- | The name of the header |
| description | any | No |  | The description of the header |
| required | any | No | false | Is the header required |
| default | any | No |  | The default value of the header |
| type | any | No | string | The type of the header |


## Set All Headers

Set all the required headers of a resource

###Arguments

| Argument | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| headers | any | Yes | --- | Set the headers of a resource |


