---
sidebar_position: 3
---

# Errors

**Schedify** uses conventional HTTP response codes to indicate the success or failure of an API request. As a general rule:
- Codes in the 2xx range indicate success.
- Codes in the 4xx range indicate incorrect or incomplete parameters (e.g. a required parameter was omitted, or an operation failed with a 3rd party, etc.).
- Codes in the 5xx range indicate an error with Schedify's servers.

**Schedify** also outputs an error message and an error code formatted in JSON:

```json
{
  "status": 0,
  "message": "An error message",
  "code": "database_error" | "server_error" | "validation_error" | "payload_error",
  "debug": "Detailed error message"
}
```
