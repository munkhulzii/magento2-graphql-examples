## Add product in cart
A customer token needed for doing cart request. You can check in customer.md how you can get the customer token.
Request type POST:
```
mutation {
  addSimpleProductsToCart(
    input: {
      cart_id: "jYJYNWfP6I6AtJUWcEZe56TieyE57rzE"
      cart_items: [
        {
          data: {
            quantity: 1
            sku: "testproduct"
          }
        }
      ]
    }
  ) {
    cart {
      items {
        id
        product {
          sku
          stock_status
        }
        quantity
      }
    }
  }
}
```
Response:
```
{
  "data": {
    "addSimpleProductsToCart": {
      "cart": {
        "items": [
          {
            "id": "1",
            "product": {
              "sku": "Testproduct",
              "stock_status": "IN_STOCK"
            },
            "quantity": 1
          }
        ]
      }
    }
  }
}
```

## Get customer cart
Request type GET:
```
{
  customerCart{
    id,
    items {
      id
      product {
        id
        sku
        name
      }
    }
  }
}
```
Response: 
```
{
  "data": {
    "customerCart": {
      "id": "jYJYNWfP6I6AtJUWcEZe56TieyE57rzE",
      "items": [
        {
          "id": "1",
          "product": {
            "id": 1,
            "sku": "Testproduct",
            "name": "Testproduct"
          }
        }
      ]
    }
  }
}
```
