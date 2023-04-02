# [🔙 Home](Readme.md)

# Get-list-books

## 👉 Response

✅ Status Code: 200
```json
[
    {
        "id": int,
        "title": string,
        "topic": string,
        "authorName": string,
        "publishYear": int,
        "price": decimal,
        "rating": int
    }
]
```

❌ Status Code: 400
```json
{
    "message": string
}
```

## 👉 Sample API

<table>
<tr>
<td>Method</td>
<td>API </td>
<td>Descriptions </td>
<td>Status code</td>
<td>Response body</td>
</tr>

<tr>
<td>GET </td>
<td>/api/books </td>
<td>Get all books </td>
<td>200</td>
<td>

```json
[
      {
        "id": 1,
        "title": "Act like a Lady, Think like a Man",
        "topic": "relationship",
        "authorName": "Steve Harvey",
        "publishYear": 2009,
        "price": 20.00,
        "rating" : 1
    },
    ...
]
```

</td>
</tr>

<tr>
<td>GET </td>
<td>/api/books?authorId=1 </td>
<td>Get list books by Author</td>
<td>200</td>
<td>

```json
[
      {
        "id": 1,
        "title": "Act like a Lady, Think like a Man",
        "topic": "relationship",
        "authorName": "Steve Harvey",
        "publishYear": 2009,
        "price": 20.00,
        "rating" : 1
    },
    ...
]
```

</td>
</tr>

<tr>
<td>GET </td>
<td>/api/books?rating=1 </td>
<td>Get list books by Rating</td>
<td>200</td>
<td>

```json
[
      {
        "id": 1,
        "title": "Act like a Lady, Think like a Man",
        "topic": "relationship",
        "authorName": "Steve Harvey",
        "publishYear": 2009,
        "price": 20.00,
        "rating" : 1
    },
    ...
]
```

</td>
</tr>

<tr>
<td>GET </td>
<td>/api/books?publishYear=2009 </td>
<td>Get list books by Rating</td>
<td>200</td>
<td>

```json
[
      {
        "id": 1,
        "title": "Act like a Lady, Think like a Man",
        "topic": "relationship",
        "authorName": "Steve Harvey",
        "publishYear": 2009,
        "price": 20.00,
        "rating" : 1
    },
    ...
]
```

</td>
</tr>

</table>

# Get-detail-book

## 👉 Response

✅ Status Code: 200
```json
{
    "id": int,
    "title": string,
    "topic": string,
    "author": {
        "id": int,
        "name": string,
        "female": boolean,
        "bornYear": int,
        "diedYear": int,
        "age": int // Calculates based on current year if they are alive,
        // otherwise based on year of death.
    },
    "publishYear": int,
    "price": decimal,
    "rating": int
}
```

❌ Status Code: 404
```json
{}
```

## 👉 Sample API

<table>
<tr>
<td>Method</td>
<td>API </td>
<td>Descriptions </td>
<td>Status Code </td>
<td>Response body</td>
</tr>

<tr>
<td>GET </td>
<td>/api/books/15 </td>
<td>Get book by Id </td>
<td>200</td>
<td>

```json
{
    "id": 15,
    "title": "The Power of Positive Thinking",
    "topic": "optimism",
    "author": {
        "id": 14,
        "name": "David Schwartz",
        "female": false,
        "bornYear": 1927,
        "diedYear": 1987,
        "age": 60 // Calculates based on current year if they are alive,
        // otherwise based on year of death.
    },
    "publishYear": 1952,
    "price": 12.34,
    "rating": 5
}
```

</td>
</tr>

<tr>
<td>GET </td>
<td>/api/books/30 </td>
<td>Get book by Id (if not found)</td>
<td>404</td>
<td>
None
</td>
</tr>
</table>

# Create-book

## 👉 Request Body

```json
{
    "title": string (required),
    "topic": string (optional),
    "authorId": int (required),
    "publishYear": int (optinal),
    "price": decimal (optional - default:0),
    "rating": int (optional)
}
```

## 👉 Response Body

✅ Status Code: 200
```json
{}
```

❌ Status Code: 400
```json
{
    "message": string
}
```

## 👉 Sample API
<table>
<tr>
<td>Method</td>
<td>API </td>
<td>Descriptions </td>
<td>Request Body </td>
<td>Status Code </td>
<td>Response body</td>
</tr>

<tr>
<td>POST </td>
<td>/api/books </td>
<td>Create new book </td>
<td>

```json
{
    "title": "The Alchemist",
    "topic": "optimism",
    "authorId": 30,
    "publishYear": 1988,
    "price": 50.05,
    "rating": 5
}
```

</td>
<td>201</td>
<td>None</td>
</tr>

<tr>
<td>POST </td>
<td>/api/books </td>
<td>Create new book with invalid authorId </td>
<td>

```json
{
    "title": "The Alchemist",
    "topic": "optimism",
    "authorId": 100,
    "publishYear": 1988,
    "price": 50.05,
    "rating": 5
}
```

</td>
<td>400</td>
<td>

```json
{
    "message": "Author is not found"
}
```

</td>
</tr>

<tr>
<td>POST </td>
<td>/api/books </td>
<td>Create new book with duplicate name </td>
<td>

```json
{
    "title": "The Secret",
    "topic": "optimism",
    "authorId": 16,
    "publishYear": 2006,
    "price": 20.5,
    "rating": 4
}
```

</td>
<td>400</td>
<td>

```json
{
    "message": "There are already other items in the database with the same name."
}
```

</td>
</tr>   
</table>




# Update-book

## 👉 Request Body

```json
{
    "title": string (required),
    "topic": string (optional),
    "authorId": int (required),
    "publishYear": int (optinal),
    "price": decimal (optional - default:0),
    "rating": int (optional)
}
```
## 👉 Response Body

✅ Status Code: 200
```json
{}
```

❌ Status Code: 400
```json
{
    "message": string
}
```

## 👉 Sample API

<table>
<tr>
<td>Method</td>
<td>API </td>
<td>Descriptions </td>
<td>Request Body </td>
<td>Status Code </td>
<td>Response body</td>
</tr>

<tr>
<td>PUT </td>
<td>/api/books/1 </td>
<td>Update existing book </td>
<td>

```json
{
    "title": "Act like a Lady, Think like a Man",
    "topic": "relationship",
    "authorId": 1,
    "publishYear": 2009,
    "price": 50.05,
    "rating": 5
}
```

</td>
<td>200</td>
<td>

```json
{
    "id": 1,
    "title": "Act like a Lady, Think like a Man",
    "topic": "relationship",
    "author": {
        "id": 1,
        "name": "Steve Harvey ",
        "female": false,
        "bornYear": 1957,
        "diedYear": null,
        "age": 66 // Calculates based on current year if they are alive,
        // otherwise based on year of death.
    },
    "publishYear": 2009,
    "price": 50.05,
    "rating": 5
}
```

</td>
</tr>

<tr>
<td>PUT </td>
<td>/api/books/1 </td>
<td>Update existing book with invalid authorId </td>
<td>

```json
{
    "title": "Act like a Lady, Think like a Man",
    "topic": "relationship",
    "authorId": 2,
    "publishYear": 2009,
    "price": 50.05,
    "rating": 5
}
```

</td>
<td>400</td>
<td>

```json
{
    "message": "Author is not found"
}
```

</td>
</tr>

</table>

# Delete-book

## 👉 Response Body

✅ Status Code: 200
```json
{}
```

❌ Status Code: 400
```json
{
    "message": string
}
```

## 👉 Sample API


<table>
<tr>
<td>Method</td>
<td>API </td>
<td>Descriptions </td>
<td>Request Body </td>
<td>Status Code </td>
<td>Response body</td>
</tr>

<tr>
<td>DELETE </td>
<td>/api/books/1 </td>
<td>Delete existing book </td>
<td>None</td>
<td>200</td>
<td>None</td>
</tr>

<tr>
<td>DELETE </td>
<td>/api/books/100 </td>
<td>Update existing book (item does not exist) </td>
<td>None </td>
<td>404</td>
<td>None</td>
</tr>

</table>

# Get-authors


## 👉 Response Body

✅ Status Code: 200
```json
[
    {
        "id": int,
        "name": string,
        "female": boolean,
        "bornYear": int,
        "diedYear": int,
        "age": int // Calculates based on current year if they are alive,
        // otherwise based on year of death.
    }
]
```

## 👉 Sample API

<table>

<tr>
<td>Method</td>
<td>API </td>
<td>Descriptions </td>
<td>Request Body </td>
<td>Status Code </td>
<td>Response body</td>
</tr>

<tr>
<td>GET </td>
<td>/api/authors </td>
<td>Get list of author </td>
<td>None </td>
<td>200</td>
<td>

```json
[
    {
        "id": 1,
        "name": "Steve Harvey ",
        "female": false,
        "bornYear": 1957,
        "diedYear": null,
        "age": 66 // Calculates based on current year if they are alive,
        // otherwise based on year of death.
    }
]
```

</td>
</tr>
</table>
