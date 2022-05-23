# Saving Quiz Results

Every time a student studies an item in your system, you should send the results to our learning engine. This will allow our system to make predictions about various things for the student and also for the items that are being studied. Our system learns what items are easy or hard for a particular student and as multiple students study, it also learns which items are harder or easier than other items. It can use this information to make predictions about which items are the optimal items that a student should review, as well as predict a student’s “readiness score” for each item.

## Save the results of a user studying an item

```shell
curl 'https://partners.cerego.com/v3/study' \
 -X POST \
 -H 'Authorization: Bearer <API_KEY>' \
 -H 'Content-Type: application/json' \
 -d '{"user_id":"1185304", "partner_id": "779", "study_time_millis":4930, "learning_engine_guid":"4ec0d7e2-a986-487d-9682-9ba6bbcb4cea", "quiz_result":"Correct"}'
```

> The above command returns a 204 status code if successful

### HTTP Request

`POST https://partners.cerego.com/v3/study`

### Request Parameters

| Parameter            | Description                                                                                                                                                                                                                                      |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| user_id              | The Cerego ID of the user who performed the study                                                                                                                                                                                                |
| partner_id           | The ID of your partner account                                                                                                                                                                                                                   |
| learning_engine_guid | The learning engine GUID of the item that was studied                                                                                                                                                                                            |
| quiz_result          | Should be "Correct" or "Incorrect". Optionally, you can specify "AlmostCorrect" if the user wasn't correct, but was close (eg. a spelling quiz where the user misses only one letter)                                                            |
| study_time_millis    | The number of milliseconds the user spent on an item. Using a typical multiple choice question as an example, this would be the total time including reading the question, answering, as well as time spent viewing if they were correct or not. |

### HTTP Response

Responds with a 204 status code if successful.
