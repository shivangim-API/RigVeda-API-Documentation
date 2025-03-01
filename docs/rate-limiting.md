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

Client Recommendation
Implement exponential backoff retry strategies to avoid continuous 429 errors.


---

# 📄 **docs/sample-requests.md**

```md
# Sample Requests & Responses

## Example 1 - Retrieve Verses by Mandal and Sukta
### Request
```bash
curl -X GET "https://sheetlabs.com/IND/rv?mandal=7&sukta=43" \
     -H "Content-Type: application/json"
Response

[
    {
        "mandal": 7,
        "sukta": 43,
        "sungby": "Vasishth Maitravaruni",
        "sungbycategory": "human male",
        "sungfor": "Vishwadeva",
        "sungforcategory": "divine male",
        "meter": "Trishtup"
    }
]


---

# 📄 **docs/openapi.yaml** (Optional - Example OpenAPI Spec)

```yaml
openapi: 3.0.0
info:
  title: Rig Veda API
  version: 1.0.0
  description: Provides access to verses from the Rig Veda, an ancient Indian text.

paths:
  /rv:
    get:
      summary: Retrieve verses from the Rig Veda
      parameters:
        - name: mandal
          in: query
          description: Mandal (Book) number
          schema:
            type: integer
        - name: sukta
          in: query
          description: Sukta (Hymn) number
          schema:
            type: integer
        - name: sungby
          in: query
          description: Composer's name
          schema:
            type: string
        - name: meter
          in: query
          description: Verse meter
          schema:
            type: string
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              example:
                - mandal: 7
                  sukta: 43
                  sungby: "Vasishth Maitravaruni"
                  meter: "Trishtup"
        '404':
          description: Not Found
