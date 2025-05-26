# Secure Audit API Documentation

## Overview

The Secure Audit API provides endpoints to manage and retrieve audit logs for your applications. All requests must be authenticated.

---

## Authentication

All endpoints require a valid API key in the `Authorization` header:

```
Authorization: Bearer YOUR_API_KEY
```

---

## Endpoints

### 1. Get Audit Logs

- **Endpoint:** `GET /api/audit/logs`
- **Description:** Retrieves a list of audit logs.
- **Query Parameters:**
    - `start` (optional, ISO 8601): Start date filter.
    - `end` (optional, ISO 8601): End date filter.
    - `userId` (optional): Filter by user ID.
- **Response:**
    ```json
    [
        {
            "id": "string",
            "timestamp": "2025-05-26T12:00:00Z",
            "userId": "string",
            "action": "string",
            "details": "string"
        }
    ]
    ```

---

### 2. Get Audit Log by ID

- **Endpoint:** `GET /api/audit/logs/{id}`
- **Description:** Retrieves a specific audit log entry.
- **Response:**
    ```json
    {
        "id": "string",
        "timestamp": "2025-05-26T12:00:00Z",
        "userId": "string",
        "action": "string",
        "details": "string"
    }
    ```

---

### 3. Create Audit Log

- **Endpoint:** `POST /api/audit/logs`
- **Description:** Creates a new audit log entry.
- **Request Body:**
    ```json
    {
        "userId": "string",
        "action": "string",
        "details": "string"
    }
    ```
- **Response:** `201 Created`

---

## Error Responses

- `401 Unauthorized`: Invalid or missing API key.
- `404 Not Found`: Resource does not exist.
- `400 Bad Request`: Invalid input.

---

## Contact

For support, contact [ei@nsisong.com](mailto:ei@nsisong.com).