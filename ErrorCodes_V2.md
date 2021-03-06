# AMPnet API Error Response Docs

# Introduction

AMPnet backend returns error response when errors happen (duh). 
Error response contains:
* `err_code` - structured in a way that should be easy to read and identify on-the-fly, 
* `description` - defined in the tables below,
* `message` - generated depending on the problem and provides more information.

Each error code consists of two parts:
1. Two digits for error category,
2. Two digits for specific error withing the category.

## Example

Specific Error: `Registration incomplete`

Error category code: `01`

Error specific code: `01`

Full error code: `0101`

Description: `Invalid signup data`

Message: `Missing UserInfo with session id: 44927492-8799-406e-8076-933bc9164ebc`

JSON Response example: 

```
{
  err_code: "0101",
  description: "Invalid signup data",
  message: "Missing UserInfo with session id: 44927492-8799-406e-8076-933bc9164ebc"
}
```

## Error code categories with prefixes

| Category       | Prefix |
|----------------|--------|
| Registration   | 01     |
| Authentication | 02     |
| User           | 03     |
| Cms            | 04     |

### Registration - Prefix: 01

| Error Description                               | Error Code |
|-------------------------------------------------|------------|
| Invalid signup data                             | 01         |
| Missing Veriff session.                         | 02         |

### Authentication - Prefix: 02

| Error Description               | Error Code |
|---------------------------------|------------|
| Invalid refresh token           | 01         |
| Payload missing                 | 02         |
| Signed payload invalid          | 03         |

### Users - Prefix: 03

| Error Description                                             | Error Code |
|---------------------------------------------------------------|------------|
| Missing user defined in JWT                                   | 01         |

### Cms - Prefix: 04

| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Required field in mail is missing                                                     | 01         |
| Mail type is not defined                                                              | 02         |
| Language is not defined                                                               | 03         |
| Content is not found                                                                  | 04         |

# Web3Provider

Web3Provider service is a proxy caching service to the blockchain. Providers take JSON-RPC requests and return a response.
Specification for error codes can be found on https://eth.wiki/json-rpc/json-rpc-error-codes-improvement-proposal.
