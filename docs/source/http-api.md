# HTTP API

Metl provides an HTTP API to perform CRUD operations (Create,Read,Update,Delete), also to manage the cache:

| Endpoint Starting | Type | Usage
|-|-|-|
| `/one/`... | REST API | One item operations |
| `/many/`... | HTTP API | One or many items operations |
| `/cache/`... | HTTP API | Cache operations |

## `/one/`

//TODO:

---
## `/many/`

Used to perfom CRUD opertation for one or many items. Endpoints are discribed below:

| Endpoint | Method | Usage
|-|-|-|
| /many/create/`schema`/`entity` | POST | Creates one or many items |
| /many/read/`schema`/`entity` | POST | Returns one or many items |
| /many/update/`schema`/`entity` | POST | Updates one or many items |
| /many/delete/`schema`/`entity` | POST | Deletes one or many items |


# Endpoint name

Method | syntax
----- | ----------
GET | base_url/endpoint/etc.

<!-- Delete this comment after you have replaced the method and syntax above. -->

## Description

<!-- Enter a short description. What is it for, and what can it do? -->

Parameters

Name | type | Req. | Description
---- | ----- | ----- | --------------------
Parameter_one | string | Y |  Stores the customer name
Parameter_two | int  | N | Stores a postal code, like the U.S. ZIP code.

<!-- Replace the two example rows and include rows for all your parameters. -->
<!-- If one of the parameters has a set of sub-parameters, create a table or bulleted list for that, but proceed with caution. If the API is complex, there might be an easier way to do your reference section than writing markup by hand. -->

## Examples

### Request

```HTTP
<!--  A copy-and-paste working request, if possible. Not one with values replaced by their names, such as "ID." -->

```

<!-- Follow with comments to explain what each part of the request is doing -->

### Response

```HTTP
<!--  An actual response returned by this endpoint for the request above.  -->

```

<!-- Write a comment explaining the response, if it would be helpful. For a response with a complicated schema, create a table like the one used above for the request.  -->

### `/many/create/`
//TODO:

`create` is used to create one or many objects in the entity provided in parameters:

```
POST /many/create/schema/entity
```

Example:
```
POST /many/create/postgres-db1/media
Content-Type: application/json

{
	"data": {
		"name":"Facebook",
		"color": 1
	}
}
```

It is possible to use options to apply filtering such as the options `filter` and `filterExpression`, or caching with the option `cache` (See: [Options](#Options))

### `/many/read/`

By default, `read` return all available data in the entity provided in parameters:

```
POST /many/read/schema/entity
```

It is possible to use options to apply filtering such as the options `filter` and `filterExpression`, or caching with the option `cache` (See: [Options](#Options))


### `/many/update/`
//TODO:
By default, `read` return all available data in the entity provided in parameters:

```
POST /many/read/schema/entity
```

It is possible to use options to apply filtering such as the options `filter` and `filterExpression`, or caching with the option `cache` (See: [Options](#Options))



### `/many/delete/`
//TODO:


```
POST /many/delete/schema/entity
```

It is possible to use options to apply filtering such as the options `filter` and `filterExpression`, or caching with the option `cache` (See: [Options](#Options))

---
## <a name="Options"></a>Options

Options are usefull for applying filtering, sorting or limit fields to return.
By sending JSON object in the body containing different options.

>** *Note:* **
>*All options are passed to the data source to be treated, except for `cache` directive that is handled by Metl Server.*


All options are described in the table below:

| Option | Usage | create | read | update | delete |
|-|-|-|-|-|-|
| `filter` | simple filter | | :fa-check-circle: | :fa-check-circle: | :fa-check-circle: |
| `filterExpression` | complex filter expression | | :fa-check-circle: | :fa-check-circle: | :fa-check-circle: |
| `fields` | select fields to return | | :fa-check-circle: | | |
| `sort` | sort data with given order | | :fa-check-circle: | | |
| `cache` | cache returned data for given time | | :fa-check-circle: | | |

#### filter

`filter` is a simple filtering feature by providing fields and equality.

Example:
To filter people with name `John` and location in `France`:

```
POST /many/read/schema/entity
Content-Type: application/json

{
	"filter": {
		"Name": "John",
		"Location": "France"
	}
}
```

#### filterExpression

`filterExpression` is used for more complex data filtering.

Metl uses a custom boolean language designed to be provider-neutral allowing it to be translated in the selected provider symantic at API call. This was choosen to maximize compliancy in case of data portability or providers mixing.

Example:

```
POST /many/read/schema/entity
Content-Type: application/json

{
	"filterExpression": "name ~ '*ing' "
}
```

For more details about Metl Neutral-Language, see : ...

It is possible to use boolean operators :

| Operator | Usage | SQL like |
|-|-|-|
| `&` | AND operator | AND |
| `|` | OR operator | OR |
| `~` | Contains operator | LIKE|

or wildcard characters :

| Character | Usage | SQL like |
|-|-|-|
| `*` | Wildcard character ( 0 or many ) | % |


#### fields

select fields to return

Example:

```
POST /many/read/schema/entity
Content-Type: application/json

{
	"filterExpression": "name ~ '*ing' "
}
```

#### sort

sort data with given order.

> ** *Note:* **
> The sorting will be executed in the backend server configured as provider, except for sources that relie on `plan` instruction, in this case Metl will performs the sorting according to the parameter. 

Example:

```
POST /many/read/schema/entity
Content-Type: application/json

{
	"sort": "name +, email -"
}
```

| Sorting Operator | Usage | SQL like |
|-|-|-|
| `+` | Ascending order | ASC |
| `-` | Descending order | DESC |

#### cache

Instruct Metl to cache  the data returned from the source for a given time in seconds before displaying it to the user end point, meanwhile users that hit again the same query will receive the cached data until it expires.

Example:

```
POST /many/read/schema/entity
Content-Type: application/json

{
	"cache": "60"
}
```
## `/cache/`



## object JSON return
## error codes


# Endpoint name

Method | syntax
----- | ----------
GET | base_url/endpoint/etc.

<!-- Delete this comment after you have replaced the method and syntax above. -->

## Description

<!-- Enter a short description. What is it for, and what can it do? -->

Parameters

Name | type | Req. | Description
---- | ----- | ----- | --------------------
Parameter_one | string | Y |  Stores the customer name
Parameter_two | int  | N | Stores a postal code, like the U.S. ZIP code.

<!-- Replace the two example rows and include rows for all your parameters. -->
<!-- If one of the parameters has a set of sub-parameters, create a table or bulleted list for that, but proceed with caution. If the API is complex, there might be an easier way to do your reference section than writing markup by hand. -->

## Examples

### Request

```HTTP
<!--  A copy-and-paste working request, if possible. Not one with values replaced by their names, such as "ID." -->

```

<!-- Follow with comments to explain what each part of the request is doing -->

### Response

```HTTP
<!--  An actual response returned by this endpoint for the request above.  -->

```

<!-- Write a comment explaining the response, if it would be helpful. For a response with a complicated schema, create a table like the one used above for the request.  -->