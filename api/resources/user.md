# Users Resource

`@me` — current user

## Upload user's tournament result

`POST /users/@me/result`

* headers:

  `Authorization: Basic {{token}}`
* data:

  JSON Params:

  | Field   | Type                     | Description |
  |---------|--------------------------|-------------|
  | results | array of participant IDs |             |

  Example:

  ```json
  {
    "results": [
      "participant1Id",
      "participant2Id"
    ]
  }
  ```

* result:
  * 200 Success
    * content: -
  * 404 Unauthorized
    * content: -
