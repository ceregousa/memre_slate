# Saving Quiz Results

Every time a user studies an item in your learning environment, you should send the results to our learning engine (remember that an item is anything which the user can get correct, incorrect, or almost correct). This allows the Memre learning engine to make predictions for the student about other learning items. For example, the system could tell the user that they aren’t ready for an advanced lesson (by reporting a lower readiness score) but that they should take the next lesson and quiz at 4pm on Wednesday (when they have tended to perform best). In fact, the Memre learning engine can constantly change and update readiness scores for all upcoming lessons. These scores can dynamically change based on the student’s performance in other lessons analyzed against the difficulty of the learning concepts.

## Save the results of a user studying an item

```shell
curl 'https://partners.cerego.com/v3/study' \
 -X POST \
 -H 'Authorization: Bearer <API_KEY>' \
 -H 'Content-Type: application/json' \
 -d '{"user_id":"1185304", "partner_id": "779", "study_time_millis":4930, "item_id":"87663", "quiz_result":"Correct"}'
```

> The above command returns a 204 status code if successful

### HTTP Request

`POST https://partners.cerego.com/v3/study`

### Request Parameters

| Parameter         | Description                                                                                                                                                                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| user_id           | The Memre ID of the user who performed the study                                                                                                                                                                                                 |
| partner_id        | The ID of your partner account                                                                                                                                                                                                                   |
| item_id           | The ID of the item that was studied                                                                                                                                                                                                              |
| quiz_result       | Should be "Correct" or "Incorrect". Optionally, you can specify "AlmostCorrect" if the user wasn't correct, but was close (eg. a spelling quiz where the user misses only one letter)                                                            |
| study_time_millis | The number of milliseconds the user spent on an item. Using a typical multiple choice question as an example, this would be the total time including reading the question, answering, as well as time spent viewing if they were correct or not. |

### HTTP Response

Responds with a 204 status code if successful.
