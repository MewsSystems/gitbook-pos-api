# Features

The __Mews POS API__ has the following notable features:

- Versioned
- Authenticated
- Uses cursor pagination (depending on the operation)
- Follows the [JSON:API specification](https://jsonapi.org/)

Mews POS API follows to the [JSON:API specification](https://jsonapi.org/) and is REST-based. JSON:API specification requires the use of (application/vnd.api+json) media type for data exchange between the client and the server.

The Mews API currently supports the following JSON:API features:

- [Relationships](./relationships.md)
- [Filtering](./filtering.md)
- [Sparse fieldsets](./sparse-fieldsets.md)

Resources in Mews API include the following:

- [Invoices](../operations/invoices.md)
- [Products](../operations/products.md)
- [Registers](../operations/registers.md)

