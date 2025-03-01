# Error Handling

The API uses conventional HTTP response codes to indicate the success or failure of requests.

| Status Code | Description                                           |
|-------------|-------------------------------------------------------|
| 200         | OK – Request successful                               |
| 403         | Forbidden – Monthly request limit exceeded            |
| 404         | Not Found – Invalid resource name or ID               |
| 401         | Unauthorized – Invalid access token                   |
| 429         | Too Many Requests – Rate limiting triggered           |
