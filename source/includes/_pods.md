# PODS

## Register a UUID

Registers a UUID with Recursion.Space as a valid Pod identifier.
This step authorizes a Pod UUID under the user's account/API token, so that the device can register itself in the next step.

> `POST` /v1/pods

```shell
curl -X POST "https://api.recursion.space/v1/pods" \
  -H "Content-Type: application/json" \
  -H "Authorization: Token xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" \
  -d '{"uuid": "xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx"}'
```

### Parameters

| Field  | Type          | Required | Description                                                     |
| ------ | ------------- | -------- | --------------------------------------------------------------- |
| `uuid` | string (UUID) | true     | The unique identifier for the Pod. Must be a valid UUID format. |

> Example Successful Response (HTTP 201 Created)

```json
{
  "uuid": "xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx"
}
```

### Returns

| Field  | Type   | Description                        |
| ------ | ------ | ---------------------------------- |
| `uuid` | string | The unique identifier for the Pod. |

## Provision a Pod

Provision a Pod with Recursion.Space, this will provide the Pod with a token to use for future requests.

> `POST` /v1/pods/{uuid}/provision

```shell
curl -X POST "https://api.recursion.space/v1/pods/xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx/provision" \
  -H "Content-Type: application/json" \
  -d '{"serial": "xxxxxxxxxxxx"}'
```

### Parameters

| Field    | Type   | Required | Description                   |
| -------- | ------ | -------- | ----------------------------- |
| `serial` | string | true     | The serial number of the Pod. |

> Example Successful Response (HTTP 201 Created)

```json
{
  "uuid": "xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "serial": "xxxxxxxx",
  "token": "pod_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
}
```

### Returns

| Field    | Type   | Description                                 |
| -------- | ------ | ------------------------------------------- |
| `uuid`   | string | The unique identifier for the Pod.          |
| `serial` | string | The serial number of the Pod.               |
| `token`  | string | The Pod's unique token for future requests. |

<aside class="warning">
The Pod token is unique to each Pod and must be kept secure. If the Pod token is lost or compromised, it cannot be reset. In such cases, you will need to re-provision the Pod by deleting the UUID and re-provisioning the Pod.
</aside>
