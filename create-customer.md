Request:

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
