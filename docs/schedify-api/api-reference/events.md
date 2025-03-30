# Events API
Manage events and tasks using Schedify’s Webhooks API.

## Endpoints
- **[Create an Event](#create-an-event)** – Schedule a new event.
- **[List All Events](#list-all-events)** – Retrieve all scheduled events.

---

## Create an Event
Create a new event that will be executed at a specified time.

### **Request**
**Method:** `POST`
**URL:**
```plaintext
https://api.schedify.dev/v1/webhooks/WEBHOOK_ID/events
```
**Headers:**
```http
Authorization: Bearer <api_key>
Content-Type: application/json
```
**Body:**
```json
{
  "event_name": "string",
  "payload": { } | null,
  "scheduled_for": "ISO_STRING"
}
```
📌 **Notes:**
- `scheduled_for` must be in [ISO 8601 format](https://en.wikipedia.org/wiki/ISO_8601), e.g., `"2025-04-01T12:00:00Z"`.
- `payload` must be a **valid JSON object** (`{}`) or `null`.

### **Example Request (cURL)**
```bash
curl -L \
  --request POST \
  --url 'https://api.schedify.dev/v1/webhooks/WEBHOOK_ID/events' \
  --header 'Authorization: Bearer <api_key>' \
  --header 'Content-Type: application/json' \
  --data '{
    "event_name": "user_signup",
    "payload": {"userId": 123},
    "scheduled_for": "2025-04-01T12:00:00Z"
  }'
```

#### **Example with `null` payload**
```bash
curl -L \
  --request POST \
  --url 'https://api.schedify.dev/v1/webhooks/WEBHOOK_ID/events' \
  --header 'Authorization: Bearer <api_key>' \
  --header 'Content-Type: application/json' \
  --data '{
    "event_name": "system_maintenance",
    "payload": null,
    "scheduled_for": "2025-04-01T12:00:00Z"
  }'
```

### **Response**
**Status:** `200 OK`
```json
{
  "status": 1,
  "message": "",
  "data": {
    "eventId": "string"
  }
}
```

---

## List All Events
Retrieve a paginated list of all scheduled events.

### **Request**
**Method:** `GET`
**URL:**
```plaintext
https://api.schedify.dev/v1/webhooks/WEBHOOK_ID/events?page=0
```
**Headers:**
```http
Authorization: Bearer <api_key>
```

### **Example Request (cURL)**
```bash
curl -L \
  --url 'https://api.schedify.dev/v1/webhooks/WEBHOOK_ID/events?page=0' \
  --header 'Authorization: Bearer <api_key>'
```

### **Response**
**Status:** `200 OK`
```json
{
  "status": 1,
  "events": [
    {
      "id": "string",
      "event_name": "string",
      "status": "string",
      "payload": {},  // or null
      "scheduled_for": 1743343719, // Unix epoch time
      "processed_at": 1743343719, // Unix epoch time
      "error_reason": null,
      "created_at": 1743343719, // Unix epoch time
      "updated_at": 1743343719, // Unix epoch time
      "webhook_id": 123
    }
  ],
  "count": 10
}
```

### **Response Fields**
| Field            | Type             | Description |
|-----------------|----------------|-------------|
| `status`       | `number`        | API response status (1 = success). |
| `events`       | `array`         | List of scheduled events. |
| `id`           | `string`        | Unique event identifier. |
| `event_name`   | `string`        | Name of the event. |
| `status`       | `string`        | Event status (`PENDING`, `DELIVERED`, `ERRORED`, `CANCELLED`). |
| `payload`      | `object/null`   | Custom data associated with the event or `null` if no data. |
| `scheduled_for` | `number`       | Scheduled execution time (Unix timestamp format). |
| `processed_at` | `number/0`   | Time event was processed (Unix timestamp format). |
| `error_reason` | `string/null`   | Error message if the event failed. |
| `created_at`   | `number`        | Event creation timestamp (Unix timestamp format). |
| `updated_at`   | `number`        | Last update timestamp (Unix timestamp format). |
| `webhook_id`   | `number`        | Associated webhook ID. |
| `count`        | `number`        | Total number of events. |

---

## Notes
- **Authentication:** All requests require a valid API key in the `Authorization` header.
- **Time Format:** `scheduled_for`, `processed_at`, `created_at`, and `updated_at` use **ISO 8601 format** (`YYYY-MM-DDTHH:mm:ssZ`).
- **Payload Requirement:** Must be a **valid JSON object** or `null`.
- **Pagination:** Use the `page` query parameter to navigate results (`?page=0`, `?page=1`, etc.).
