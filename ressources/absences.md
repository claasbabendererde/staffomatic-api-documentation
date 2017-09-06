Absences
=======================

Get absences
----------

* `GET /locations/64/absences.json` will return all absences for specified location
* `GET /absences.json?user_ids%5B%5D=493` will return absences for the specified user
* `GET /absences.json?from=2016-03-31T22%3A00%3A00.000Z&until=2016-06-29T22%3A00%3A00.000Z` will return between datetime range
* `GET /absences.json?absence_type_id%5B%5D=1` will return absences for the absence type
* `GET /absences.json?paid=true` will return paid absences
* `GET /absences.json?vacation=true` will return absences specified as vacation
* `GET /absences.json?state%5B%5D=approved` will return absences for approved state

```json
[
  {
    "created_at": "2014-11-17T19:36:19+01:00",
    "updated_at": "2014-11-17T19:36:22+01:00",
    "id": 85015,
    "starts_at": "2014-11-16T00:00:00+01:00",
    "ends_at": "2014-11-23T23:59:59+01:00",
    "processed_at": "2014-11-17T19:36:22+01:00",
    "paid": false,
    "vacation": true,
    "state": "approved",
    "include_weekends": false,
    "comments_count": 0,
    "attachments_count": 0,
    "commentable": true,
    "attachable": true,
    "all_day": true,
    "justification": "",
    "last_updated_by_id": 493,
    "adjusted_duration": 691200,
    "comment_ids": [ ],
    "attachment_ids": [ ],
    "applicant_id": 493,
    "handler_id": 493,
    "location_id": 64,
    "absence_type_id": 1
  }
]
```

Get absence
----------

* `GET /locations/64/absences/85015.json` will return the specified absence.

```json
{
  "created_at": "2014-11-17T19:36:19+01:00",
  "updated_at": "2014-11-17T19:36:22+01:00",
  "id": 85015,
  "starts_at": "2014-11-16T00:00:00+01:00",
  "ends_at": "2014-11-23T23:59:59+01:00",
  "processed_at": "2014-11-17T19:36:22+01:00",
  "paid": false,
  "vacation": true,
  "state": "approved",
  "include_weekends": false,
  "comments_count": 0,
  "attachments_count": 0,
  "commentable": true,
  "attachable": true,
  "all_day": true,
  "justification": "",
  "last_updated_by_id": 493,
  "adjusted_duration": 691200,
  "comment_ids": [ ],
  "attachment_ids": [ ],
  "applicant_id": 493,
  "handler_id": 493,
  "location_id": 64,
  "absence_type_id": 1
}
```

Create absence
--------------

* `POST /locations/64/absences.json` will create a new absence from the parameters passed.

```json
{
  "starts_at": "2015-07-20T00:00:00+02:00",
  "ends_at": "2015-07-22T00:00:00+02:00",
  "applicant_id": 493,
  "absence_type_id": 1,
  "paid": true,
  "vacation": true,
  "include_weekends": true,
  "all_day": true,
  "justification": "I have jury duty",
  "commentable": true,
  "attachable": true
}
```

This will return `201 Created` with the current JSON representation of the absence if the creation was a success.


Update absence
--------------

* `PUT /locations/64/absences/83959.json` will update the absence from the parameters passed.

```json
{
  "starts_at": "2015-07-20T00:00:00+02:00",
  "ends_at": "2015-07-22T00:00:00+02:00",
  "applicant_id": 493,
  "absence_type_id": 1,
  "paid": true,
  "vacation": true,
  "include_weekends": true,
  "all_day": true,
  "justification": "I have jury duty",
  "commentable": true,
  "attachable": true
}
```

Approve absence
--------------

* `PUT /locations/64/absences/85018.json` will update the absence from the parameters passed.

```json
{
  "do": "approve"
}
```

add the params `"handle_applications": "destroy"` if you want to destroy all assigned applications from the user in the absence timeframe:

```json
{
  "do": "approve",
  "handle_applications": "destroy"
}
```

**Note:** You cannot update an absence after approving

Decline absence
--------------

* `PUT /locations/64/absences/83959.json` will update the absence from the parameters passed.

```json
{
  "do": "decline"
}
```

**Note:** You cannot update an absence after declining

Delete absence
--------------

* `DELETE /locations/64/absences/83959.json`

Will delete the absence specified and return 204 No Content if that was successful.
