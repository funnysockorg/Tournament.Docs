# Tournament resource

## Get participants

`GET /tournament/participants`

Returns a list of [participant](./participant.md/#participant-object) objects.

## Get result

`GET /tournament/result`

* headers:

  `Authorization: Basic {{token}}`
* result code:
  * 200 Success

    JSON Params:

    | Field   | Type                                                                           | Description |
    |---------|--------------------------------------------------------------------------------|-------------|
    | results | dictionary of [participant](./participant.md#participant-object) IDs and score |             |

    Example:

    ```json
    {
      "results": {
        "gif1Id": {
          "score": 11
        },
        "gif2Id": {
          "score": 10
        }
      }
    }
    ```

  * 404 Unauthorized
