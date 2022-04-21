# Importing Content

Content in Cerego is organized into “sets” and “items”. A set is a collection of items and can have a maximum of 200 items. An item represents an individual thing that our learning engine optimizes the studying of. An item could be a single question and answer, or it could be multiple questions and answers that all quiz the same underlying concept (like various math questions that ask the user to multiply two numbers together).

## Creating a Set

```shell
curl 'https://partners.cerego.com/v3/sets' \
 -X POST \
 -H 'Authorization: Bearer <API_KEY>' \
 -H 'Content-Type: application/json' \
 -d '{"name":"set name","partner_id":"779"}'

```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "123456",
    "type": "sets",
    "attributes": {
      "created-at": "2021-05-27T06:13:59.000Z",
      "name": "set name",
      ...
    },
    "relationships": {
      ...
    },
    "links": {
      "self": "/v3/sets/set-name"
    }
  },
  "meta": {
    "total-pages": null,
    "total-count": null
  }
}
```

This endpoint creates a set.

### HTTP Request

`POST https://partners.cerego.com/v3/sets`

### Query Parameters

| Parameter  | Description                    |
| ---------- | ------------------------------ |
| name       | The name of the set.           |
| partner_id | The ID of your partner account |

### HTTP Response

The response will include the id of the newly created set. You should save this ID for later use with other APIs.

## Creating an Item

```shell
curl 'https://partners.cerego.com/v3/sets/1002204/learning_items' \
 -X POST \
 -H 'Authorization: Bearer <API_KEY>' \
 -H 'Content-Type: application/json' \
 -d '{"question":"What is two plus two?","answer":"four"}'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "123456",
    "type": "learning-items",
    "attributes": {
      "created-at": "2021-05-27T06:13:59.000Z",
      "question": "What is two plus two?",
      "answer": "four",
      "learning-engine-guid": "e7fb6554-74a2-4d18-918c-7cf2896d265c",
      ...
    },
    "relationships": {
      ...
    },
    "links": {
      "self": "/v3/items/123456"
    }
  },
  "meta": {
    "total-pages": null,
    "total-count": null
  }
}
```

This endpoint creates an item within a set. You can optionally specify a question and answer for the item. If your item isn't a simple question with an answer, simply omit the question and answer.

### HTTP Request

`POST https://partners.cerego.com/v3/sets/:set_id/learning_items`

### Query Parameters

| Parameter | Description                                           |
| --------- | ----------------------------------------------------- |
| question  | Optional text representing the question being asked   |
| answer    | Optional text representing the answer to the question |

### HTTP Response

The response will include the item’s learning engine GUID which you will use in other API calls. The item will be created in the specified set.
