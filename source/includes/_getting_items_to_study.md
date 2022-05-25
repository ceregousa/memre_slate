# Getting Items to Study

Our learning engine can predict which items a user should review in order to maximize long term retention.

## Getting items to study for maximal knowledge retention

```shell
curl 'https://partners.cerego.com/v3/study?partner_id=779&user_id=12345&set_id=5678' \
 -H 'Authorization: Bearer <API_KEY>' \

```

> The above command returns JSON structured like this:

```json
{
  "data": [
      {
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
    ...
  ],
  "meta": {
    "total-pages": null,
    "total-count": null
  }
}
```

This endpoint returns learning items in an order that is optimal for long term retention for the user.

### HTTP Request

`GET https://partners.cerego.com/v3/study`

### Query Parameters

| Parameter  | Description                                                                                                                                                                       |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| user_id    | The id of the user you want to get learning items for                                                                                                                             |
| partner_id | The ID of your partner account                                                                                                                                                    |
| set_id     | Optional ID of the set you want to get learning items for. If not specified, the endpoint will return items which are ready for review from across all sets the user has studied. |

### HTTP Response

The response will be an array of learning items. If a set_id is specified then both items from the set the user hasn't studied yet and also items which the user studied, but are ready for review will be returned. If a set_id is not specified, then items ready for review from across all sets the user has studied will be returned.
