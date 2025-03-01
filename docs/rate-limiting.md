# Rate Limiting & Throttling

To prevent excessive requests, the Rig Veda API applies **rate limiting** using the **token bucket algorithm**.

- Each request consumes a token.
- When requests exceed the configured rate, the API returns:

HTTP 429 Too Many Requests

### Example 429 Response
```json
{
    "error": "Rate limit exceeded. Please wait before sending more requests."
}


# Sample Requests & Responses

## Example 1 - Retrieve Verses by Mandal and Sukta
### Request
```bash
curl -X GET "https://sheetlabs.com/IND/rv?mandal=7&sukta=43" \
     -H "Content-Type: application/json"

