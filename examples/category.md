# GraphQl queries for category

## Get a category
Request:
```
{
  category(id:2) {
    id
    name
    url_key
    url_path
    description
    breadcrumbs  {
          category_id
        }
    
    children_count
    children {
      name
      image
      url_key
      description

    }
  }
}
```
Response:
````
{
  "data": {
    "category": {
      "id": 2,
      "name": "Default Category",
      "url_key": "default-category",
      "url_path": null,
      "description": "<p>test desciption</p>",
      "breadcrumbs": null,
      "children_count": "0",
      "children": []
    }
  }
}
````
## Use inline fragment 
Request:
````
{
  categoryList(filters: {ids: {in: ["2"]}}) {
      ... on CategoryTree {
        id
        path
        name	
        url_path
        url_key
        description,
        include_in_menu
        product_count
        products{
          total_count
          items{
            name
            sku
          }
        }

      }
  }
}
````
Response:
````
{
  "data": {
    "categoryList": [
      {
        "id": 2,
        "path": "1/2",
        "name": "Default Category",
        "url_path": null,
        "url_key": "default-category",
        "description": "<p>test desciption</p>",
        "include_in_menu": 1,
        "product_count": 1,
        "products": {
          "total_count": 1,
          "items": [
            {
              "name": "second product",
              "sku": "second product"
            }
          ]
        }
      }
    ]
  }
}
````
## Use named fragment

Request
```
{
    categoryList(filters: {ids: {in: ["2"]}}) {
        ...Cat
    }
}
fragment Cat on CategoryTree {
    id
    name
    url_key
    url_path
    children_count
    path
    position
}
```
Response:
```
{
  "data": {
    "categoryList": [
      {
        "id": 2,
        "name": "Default Category",
        "url_key": "default-category",
        "url_path": null,
        "children_count": "0",
        "path": "1/2",
        "position": 1
      }
    ]
  }
}
```
