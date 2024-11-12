# Authentication

The __Mews POS API__ uses bearer authentication, also known as token authentication. When you make an API call, you need to include your API key in the `Authorization` header in the following format:
```
Bearer <your API key>
```
`<your api key>` is a placeholder for your key which should have `sk_test` prefix for the test environment and `sk_live` prefix for the production environment.

> **Important**: It is important to keep your API keys safe. Do not share your secret API keys in publicly accessible locations like GitHub or client-side code.

All API requests should be made over `HTTPS`, any requests made over `HTTP` will fail. Additionally, API requests that lack authentication will also fail.
