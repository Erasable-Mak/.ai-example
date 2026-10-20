# Telemetry & Runtime Logs - EXAMPLE-001

This file contains runtime logs, browser console outputs, or API response payloads for this ticket.

## Sample Console Telemetry

```text
[GET] /api/records?type=incident&status=investigating
Status: 200 OK
Response:
{
  "records": [
    {
      "id": "7f8b9a12-34cd-56ef-78ab-90cdef123456",
      "key": "INC-104",
      "title": "Redis connection pool starvation on checkout service",
      "status": "investigating",
      "createdAt": "2026-10-18T22:15:00.000Z"
    }
  ]
}
```

## Error Log Sample (If Applicable)

```text
TypeError: Cannot read properties of undefined (reading 'status')
    at IncidentStatusBadge (apps/web/src/features/dashboard/ui/IncidentStatusBadge.tsx:14:22)
    at renderWithHooks (node_modules/react-dom/cjs/react-dom.development.js:15486:18)
```
