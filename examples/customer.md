## Create customer

Request type POST:

```
mutation {
  createCustomer(
    input: {
      firstname: "John"
      lastname: "Doe"
      email: "john.doe@example.com"
      password: "SecurePassword"
      is_subscribed: true
    }
  ) {
    customer {
      firstname
      lastname
      email
      is_subscribed
    }
  }
}
```

Response:

```
{
  "data": {
    "createCustomer": {
      "customer": {
        "firstname": "John",
        "lastname": "Doe",
        "email": "john.doe@example.com",
        "is_subscribed": true
      }
    }
  }
}
```

## Login customer

Request type POST:
```
mutation {
  generateCustomerToken(email: "john.doe@example.com", password: "SecurePassword") {
    token
  }
}
```

Response:
```
{
  "data": {
    "generateCustomerToken": {
      "token": "rd1ezb7ag1naqmplik0mr7dhebq6pzfj"
    }
  }
}
```
This token can be used for further actions like create cart, add in to cart, get customer informations etc.
