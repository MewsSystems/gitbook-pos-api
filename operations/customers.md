<!-- AUTOMATICALLY GENERATED, DO NOT MODIFY -->
# Customers

## Get customers

This operation returns a list of customers

**Note:** This operation needs [Authentication](../guidelines/authentication.md) and supports the following JSON:API features:

- [Sparse fieldsets](../guidelines/sparse-fieldsets.md) - supports all fields of `customer` query parameter.

### Request

`GET` `[PlatformAddress]/api/v2/customers`

### Response

```javascript
{
  "data": [
    {
      "id": "31b14937-2524-491f-b0a0-dc0a7393ff33",
      "type": "customers",
      "attributes": {
        "email": "example@email.com",
        "fullName": "Name",
        "taxNumber": "tax1234",
        "dateOfBirth": "2024-10-24",
        "phone": "+123123123",
        "mobile": "+123123123",
        "address1": "Address",
        "address2": "Address",
        "city": "City",
        "state": "State",
        "postalCode": "10000",
        "country": "HR",
        "notes": "This is a note",
        "countrySpecificCode": "code",
        "companyName": "Company name",
        "createdAt": "2024-10-16T14:30:00Z",
        "updatedAt": "2024-10-19T14:30:00Z"
      }
    }
  ],
  "links": {
    "prev": "https://pos.mews-demo.com/api/v2/customers?page%5Bbefore%5D=NA&page%5Bsize%5D=1",
    "next": "https://pos.mews-demo.com/api/v2/customers?page%5Bafter%5D=NA&page%5Bsize%5D=1"
  }
}
```
Below is a list of all possible fields this endpoint can return including relationships fields fetched with include query parameter.

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `fullName` | string,null | optional, max length 255 characters | The full name of the customer. This can be either a personal name or a company name. |
| `companyName` | string,null | optional, max length 255 characters | The name of the company associated with the customer. |
| `taxNumber` | string,null | optional, max length 40 characters | The customer's tax identification number. |
| `email` | string,null | optional, max length 320 characters | The customer's email address. |
| `address1` | string,null | optional, max length 255 characters | The first line of the customer's address. |
| `address2` | string,null | optional, max length 255 characters | The second line of the customer's address. |
| `city` | string,null | optional, max length 100 characters | The city of the customer's address. |
| `state` | string,null | optional, max length 100 characters | The state or province of the customer's address. |
| `postalCode` | string,null | optional, max length 20 characters | The postal or ZIP code of the customer's address. |
| `country` | string,null | optional, max length 100 characters | The country of the customer's address. |
| `notes` | string,null | optional, max length 500 characters | Additional notes about the customer. |
| `phone` | string,null | optional, max length 20 characters | The customer's phone number. |
| `mobile` | string,null | optional, max length 20 characters | The customer's mobile phone number. |
| `countrySpecificCode` | string,null | optional, max length 50 characters | A unique country specific code assigned to the customer. Lottery code for example in Italy. |
| `dateOfBirth` | string,null | optional, max length 10 characters | The customer's date of birth in YYYY-MM-DD format. |

#### customer_pagination_links

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `prev` | string | required, max length 1024 characters | The link to the previous page of results. |
| `next` | string | required, max length 1024 characters | The link to the next page of results. |

## Create customer

A customer represents a person or organization that can be billed for goods or services.
Note: This operation needs [Authentication](../essential-guide/authentication.md).

### Request

`POST` `[PlatformAddress]/api/v2/customers`

```javascript
{
  "data": {
    "type": "customers",
    "attributes": {
      "fullName": "John Doe",
      "taxNumber": "123456789",
      "email": "john.doe@mews.com",
      "address1": "123 Main St.",
      "city": "Anytown",
      "state": "CA",
      "postalCode": "12345",
      "country": "US",
      "phone": "1234567890",
      "companyName": "Doe Enterprises",
      "dateOfBirth": "1970-01-01"
    }
  }
}
```

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `fullName` | string,null | optional, max length 255 characters | The full name of the customer. This can be either a personal name or a company name. |
| `companyName` | string,null | optional, max length 255 characters | The name of the company associated with the customer. |
| `taxNumber` | string,null | optional, max length 40 characters | The customer's tax identification number. |
| `email` | string,null | optional, max length 320 characters | The customer's email address. |
| `address1` | string,null | optional, max length 255 characters | The first line of the customer's address. |
| `address2` | string,null | optional, max length 255 characters | The second line of the customer's address. |
| `city` | string,null | optional, max length 100 characters | The city of the customer's address. |
| `state` | string,null | optional, max length 100 characters | The state or province of the customer's address. |
| `postalCode` | string,null | optional, max length 20 characters | The postal or ZIP code of the customer's address. |
| `country` | string,null | optional, max length 100 characters | The country of the customer's address. |
| `notes` | string,null | optional, max length 500 characters | Additional notes about the customer. |
| `phone` | string,null | optional, max length 20 characters | The customer's phone number. |
| `mobile` | string,null | optional, max length 20 characters | The customer's mobile phone number. |
| `countrySpecificCode` | string,null | optional, max length 50 characters | A unique country specific code assigned to the customer. Lottery code for example in Italy. |
| `dateOfBirth` | string,null | optional, max length 10 characters | The customer's date of birth in YYYY-MM-DD format. |

### Response

```javascript
{
  "data": {
    "id": "83f93e1c-b6e1-4040-90cf-3274b6f3c82d",
    "type": "customers",
    "attributes": {
      "fullName": "John Doe",
      "taxNumber": "123456789",
      "email": "john.doe@mews.com",
      "address1": "123 Main St.",
      "city": "Anytown",
      "state": "CA",
      "postalCode": "12345",
      "country": "US",
      "phone": "1234567890",
      "companyName": "Doe Enterprises",
      "dateOfBirth": "1970-01-01",
      "createdAt": "2024-10-16T14:30:00Z",
      "updatedAt": "2024-10-19T14:30:00Z"
    }
  }
}
```
Below is a list of all possible fields this endpoint can return including relationships fields fetched with include query parameter.

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `fullName` | string,null | optional, max length 255 characters | The full name of the customer. This can be either a personal name or a company name. |
| `companyName` | string,null | optional, max length 255 characters | The name of the company associated with the customer. |
| `taxNumber` | string,null | optional, max length 40 characters | The customer's tax identification number. |
| `email` | string,null | optional, max length 320 characters | The customer's email address. |
| `address1` | string,null | optional, max length 255 characters | The first line of the customer's address. |
| `address2` | string,null | optional, max length 255 characters | The second line of the customer's address. |
| `city` | string,null | optional, max length 100 characters | The city of the customer's address. |
| `state` | string,null | optional, max length 100 characters | The state or province of the customer's address. |
| `postalCode` | string,null | optional, max length 20 characters | The postal or ZIP code of the customer's address. |
| `country` | string,null | optional, max length 100 characters | The country of the customer's address. |
| `notes` | string,null | optional, max length 500 characters | Additional notes about the customer. |
| `phone` | string,null | optional, max length 20 characters | The customer's phone number. |
| `mobile` | string,null | optional, max length 20 characters | The customer's mobile phone number. |
| `countrySpecificCode` | string,null | optional, max length 50 characters | A unique country specific code assigned to the customer. Lottery code for example in Italy. |
| `dateOfBirth` | string,null | optional, max length 10 characters | The customer's date of birth in YYYY-MM-DD format. |
