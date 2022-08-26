# Importing Content

Content in Memre is organized into “sets” and “items”. A set is a collection of items and can have a maximum of 200 items. An item represents an individual concept that the Memre learning engine can optimize for a user. The simplest way to conceptualize this is that a set is a quiz and the items as the individual questions. But sets and items aren’t limited to just that. For example, a set can be comprised of multiple questions which all test the same concept (i.e., a number of different math questions that all test the same concept, such as multiplying by two numbers). At the root of it, an item is anything against which you can report through the Memre API if the user was correct, incorrect, or almost correct. So, in our example of a software development learning subscription, an item could be a task where a user must modify some code that is already written.

Of course, if you have questions or need help, our engineering team can assist you structure your course into sets and items.

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

### Request Parameters

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

### Request Parameters

| Parameter | Description                                           |
| --------- | ----------------------------------------------------- |
| question  | Optional text representing the question being asked   |
| answer    | Optional text representing the answer to the question |

### HTTP Response

The response will include the item’s ID which you will use in other API calls. The item will be created in the specified set.
