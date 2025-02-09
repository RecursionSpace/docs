# PODS

## Register a Pod UUID

Registers a new Pod in Recursion.Space by providing a UUID and any optional fields.

> `POST` /v1/pods

```shell
curl -X POST "https://api.recursion.space/v1/pods" \
  -H "Content-Type: application/json" \
  -H "Authorization: Token xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" \
  -d "uuid=xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx"
```

### Parameters

| Field  | Type          | Required | Description                                                     |
| ------ | ------------- | -------- | --------------------------------------------------------------- |
| `uuid` | string (UUID) | true     | The unique identifier for the Pod. Must be a valid UUID format. |

> Example Successful Response (HTTP 201 Created)

```shell
HTTP/1.1 201 Created

{
    "id": 1,
    "uuid": "xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx",
    "nickname": "",
    "serial": "",
    "version": "",
    "status": "0",
    "connection_last_made": "2025-02-09T05:59:08.947827Z",
    "snapshot": null,
    "facility": null
}
```
