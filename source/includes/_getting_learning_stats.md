# Getting Learning Stats

Our learning engine can give you info about the user's knowledge.

## Getting the predicted best times of day for the user to study

This endpoint returns an object indicating the predicted best times of day for the user to study.

```shell
curl 'https://partners.cerego.com/v3/users/123456/learning_stats?partner_id=779' \
 -H 'Authorization: Bearer <API_KEY>' \

```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "123456",
    "type": "user-learning-stats",
    "attributes": {
      "predicted-efficiency-by-hour": {
        "0": 0.6817623590590236,
        "1": 0.7392679289352317,
        "2": 0.6741286832391928,
        "3": 0.5505325348708183,
        "4": 0.5703524097996383,
        "5": 0.6401751938230529,
        "6": 0.5650987172034425,
        "7": 0.7438633079598264,
        "8": 0.5396156398191866,
        "9": 0.5216558829079918,
        "10": 0.5,
        "11": 0.5418908308550081,
        "12": 0.5,
        "13": 0.5583391320639809,
        "14": 0.6132052646002262,
        "15": 0.6806750042126359,
        "16": 0.6978540362089123,
        "17": 0.6408447467901008,
        "18": 0.5675780797573757,
        "19": 0.5945802720384398,
        "20": 0.592000126751934,
        "21": 0.6485270371342018,
        "22": 0.6147188037501468,
        "23": 0.5985007258321375
      }
    }
  },
  "meta": {
    "total-pages": null,
    "total-count": null
  }
}
```

### HTTP Request

`GET https://partners.cerego.com/v3/users/:user_id/learning_stats`

### Query Parameters

| Parameter  | Description                    |
| ---------- | ------------------------------ |
| partner_id | The ID of your partner account |

### HTTP Response

An object that includes an object with 24 values, each of which is a predicted efficiency of learning for that hour of the day. Example:
{... "predicted-efficiency-by-hour": {"0": 0.1, "1": 0.1, "2": 0.3, "3" 0.5,..., "22": 0.9, "23:" 0.2} ...}.
The values will be in the range of 0 to 1. Higher numbers correspond to better times of day for the user to study. The hours correspond to hours in UTC time.

## Getting the user's readiness score for a set

A user’s readiness score is a value between 0 and 1 indicating how likely the user will be able to recall the concepts of the set. See this [blog post](https://www.cerego.com/blog/new-feature-release-readiness-score-measures-knowledge-in-real-time) for more information.

```shell
curl 'https://partners.cerego.com/v3/users/123456/sets/943433/learning_stats?partner_id=779' \
 -H 'Authorization: Bearer <API_KEY>' \

```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "123456-943433",
    "type": "set-learning-stats",
    "attributes": { "readiness": 0.7791311472859385 }
  },
  "meta": { "total-pages": null, "total-count": null }
}
```

### HTTP Request

`GET https://partners.cerego.com/v3/users/:user_id/sets/:set_id/learning_stats`

### Query Parameters

| Parameter  | Description                    |
| ---------- | ------------------------------ |
| partner_id | The ID of your partner account |

### HTTP Response

An object that includes the readiness score of the set for that user.
