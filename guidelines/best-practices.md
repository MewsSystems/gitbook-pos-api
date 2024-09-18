# Best practices

This is some advice on best practices for using the API, regardless of your particular use case. Follow this advice for less errors and better performance.

- **4xx HTTP status codes**<br>Follow our recommendations on handling each 4xx [response code](https://mews-systems.gitbook.io/connector-api/guidelines/responses#response-codes).
If you receive a 400 response with an 'Invalid {Parameter}' message, one possible explanation is that the resource you are referencing doesn't exist - check with the enterprise for confirmation.

- **Limit use of extents**<br>Limit the amount of extents you use as much as possible. You can see an example of extents in [Get all resources](../operations/resources.md#get-all-resources). An extent represents a related entity that requires lookup into another database table, thus significantly hindering performance. If you need to use multiple extents, instead create a separate call for each individual extent.

- **Use pagination**<br>Use [pagination](https://mews-systems.gitbook.io/connector-api/guidelines/pagination) for 'get' operations wherever possible. Responses will be smaller and easier to manage, and you won't hit those [request timeouts](requests.md#request-timeouts)!

- **Use filtering**<br>Avoid retrieving the same data repetitively. Leverage filtering to retrieve just the subset of data that's relevant to you. Data past the [Editable History Window](https://help.mews.com/s/article/Mews-Glossary-for-Open-API-users?language=en_US#EditableHistoryWindow) can't be changed so it doesn't make sense to pull it repeatedly.
If there is no support for a filter you'd benefit from, reach out to us at [partnersuccess@mews.com](mailto:partnersuccess@mews.com) with a request to add it. 

