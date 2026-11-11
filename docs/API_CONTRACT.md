# Lumen Desk — Event List Pagination API Contract

**Status:** APPROVED DESIGN CONTRACT (DEC-003, 2026-10-30)  
**Implementation status:** NOT VERIFIED; this document defines the contract, not evidence that deployed code conforms.

## Endpoint

`GET /api/v1/events`

Returns the caller-authorized event list using cursor-based pagination.

## Request

| Parameter | Type | Required | Contract |
|---|---|---:|---|
| `cursor` | opaque string | No | Omit for the first page. When supplied, treat as an opaque continuation token; clients must not parse or construct it. |
| `page_size` | integer | No | Requested page size. The service applies the configured maximum. |

Configuration values in `prod-config.yaml` are `pagination.default_page_size: 25` and `pagination.max_page_size: 100`. The approved contract says the service applies the maximum; exact handling of invalid, zero, negative, or over-maximum values is an implementation question unless separately evidenced.

## Ordering

1. `created_at` descending;
2. immutable event ID ascending as a deterministic tie-breaker.

## Response

```json
{
  "items": [
    {
      "id": "evt_001",
      "name": "Community Nature Walk",
      "created_at": "2026-10-29T09:30:00Z"
    }
  ],
  "next_cursor": "opaque-continuation-token",
  "has_more": true
}
```

- `items`: events in the required order.
- `next_cursor`: opaque token for the next page; absent when there is no next page.
- `has_more`: whether another page is available.
- When `next_cursor` is absent, there is no next page (`has_more` should therefore be false).

## TypeScript contract types

These types describe the public contract only. They are not application implementation code.

```ts
export interface EventListItem {
  id: string;
  name: string;
  created_at: string;
}

export interface EventListQuery {
  cursor?: string;
  page_size?: number;
}

export interface EventListResponse {
  items: EventListItem[];
  next_cursor?: string;
  has_more: boolean;
}
```
