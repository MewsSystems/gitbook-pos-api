# Features

The __Mews POS API__ has the following notable features:

- Versioned
- Authenticated
- Follows the [JSON:API specification](https://jsonapi.org/)
- Uses cursor pagination (depending on the operation)

Mews POS API follows the [JSON:API specification](https://jsonapi.org/) and is REST-based.

JSON:API is a specification for how a client should request that resources be fetched or modified, and how a server should respond to those requests. Resources in Mews POS API include invoices, products, registers and more.

JSON:API is designed to minimize both the number of requests and the amount of data transmitted between clients and servers. This efficiency is achieved without compromising readability, flexibility, or discoverability.

JSON:API requires use of the JSON:API media type (application/vnd.api+json) for exchanging data.