# Creating a User

Every learner in your system should have a corresponding user in Cerego.

```shell
curl 'https://partners.cerego.com/v3/partners/:partner_id/users' \
 -X POST \
 -H 'Authorization: Bearer <API_KEY>' \
 -H 'Content-Type: application/json' \
 -d '{"name":"John"}'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "123456",
    "type": "users",
    "attributes": {
      "created-at": "2021-05-27T06:13:59.000Z",
      "name": "John",
      ...
    },
    "relationships": {
      ...
    },
    "links": {
      "self": "/v3/users/123456"
    }
  },
  "meta": {
    "total-pages": null,
    "total-count": null
  }
}
```

### HTTP Request

`POST https://partners.cerego.com/v3/partners/:partner_id/users`

### Query Parameters

| Parameter | Description                |
| --------- | -------------------------- |
| name      | Optional name of the user. |
| email     | Optional email of the user |

### HTTP Response

The response will include the id of the newly created user. You should save this ID for later use with other APIs.
