# Webhooks API
Manage webhooks using Schedify’s API.

## Endpoints
- **[List All Webhooks](#list-all-webhooks)** – Retrieve all webhooks.
- **[Get a Specific Webhook](#get-a-specific-webhook)** – Retrieve details of a single webhook.
- **[Delete a Webhook](#delete-a-webhook)** – Remove a webhook.

---

## List All Webhooks
Retrieve a paginated list of all webhooks.

### **Request**
**Method:** `GET`
**URL:**
```plaintext
https://api.schedify.dev/v1/webhooks
```
**Headers:**
```http
Authorization: Bearer <api_key>
```

### **Example Request (cURL)**
```bash
curl -L \
  --url 'https://api.schedify.dev/v1/webhooks' \
  --header 'Authorization: Bearer <api_key>'
```

### **Response**
**Status:** `200 OK`
```json
{
  "status": 1,
  "webhooks": [
    {
      "id": "string",
      "name": "string",
      "url": "string",
      "secret": "string",
      "user_id": "string",
      "created_at": 1711916400,
      "updated_at": 1711916700
    }
  ],
  "count": 10
}
```

### **Response Fields**
| Field         | Type            | Description |
|--------------|----------------|-------------|
| `status`     | `number`        | API response status (1 = success). |
| `webhooks`   | `array`         | List of webhooks. |
| `id`         | `string`        | Unique webhook identifier. |
| `name`       | `string`        | Webhook name. |
| `url`        | `string`        | Webhook URL. |
| `secret`     | `string`        | Secret key used for signature validation. |
| `user_id`    | `string`        | ID of the user who owns the webhook. |
| `created_at` | `number`        | Webhook creation time (Unix timestamp, in seconds). |
| `updated_at` | `number`        | Last update time (Unix timestamp, in seconds). |
| `count`      | `number`        | Total number of webhooks. |

---

## Get a Specific Webhook
Retrieve details of a single webhook by its ID.

### **Request**
**Method:** `GET`
**URL:**
```plaintext
https://api.schedify.dev/v1/webhooks/WEBHOOK_ID
```
**Headers:**
```http
Authorization: Bearer <api_key>
```

### **Example Request (cURL)**
```bash
curl -L \
  --url 'https://api.schedify.dev/v1/webhooks/WEBHOOK_ID' \
  --header 'Authorization: Bearer <api_key>'
```

### **Response**
**Status:** `200 OK`
```json
{
  "status": 1,
  "data": {
    "id": "string",
    "name": "string",
    "url": "string",
    "secret": "string",
    "user_id": "string",
    "created_at": 1711916400,
    "updated_at": 1711916700
  }
}
```

### **Response Fields**
| Field         | Type            | Description |
|--------------|----------------|-------------|
| `status`     | `number`        | API response status (1 = success). |
| `data`       | `object`        | Webhook details. |
| `id`         | `string`        | Unique webhook identifier. |
| `name`       | `string`        | Webhook name. |
| `url`        | `string`        | Webhook URL. |
| `secret`     | `string`        | Secret key used for signature validation. |
| `user_id`    | `string`        | ID of the user who owns the webhook. |
| `created_at` | `number`        | Webhook creation time (Unix timestamp, in seconds). |
| `updated_at` | `number`        | Last update time (Unix timestamp, in seconds). |
| `deleted_at` | `number/null`   | Deletion time if the webhook is deleted, otherwise `null`. |

---

## Delete a Webhook
Remove a webhook by its ID.

### **Request**
**Method:** `DELETE`
**URL:**
```plaintext
https://api.schedify.dev/v1/webhooks/WEBHOOK_ID
```
**Headers:**
```http
Authorization: Bearer <api_key>
```

### **Example Request (cURL)**
```bash
curl -L \
  --request DELETE \
  --url 'https://api.schedify.dev/v1/webhooks/WEBHOOK_ID' \
  --header 'Authorization: Bearer <api_key>'
```

### **Response**
**Status:** `200 OK`
```json
{
  "status": 1,
  "message": "Webhook successfully deleted"
}
```

### **Response Fields**
| Field      | Type     | Description |
|------------|---------|-------------|
| `status`   | `number` | API response status (1 = success). |
| `message`  | `string` | Confirmation message. |

---

## Notes
- **Authentication:** All requests require a valid API key in the `Authorization` header.
- **Time Format:** `created_at` and `updated_at` use **Unix timestamps (in seconds)**.
