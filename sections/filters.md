# Items API

> Filters.

## Available methods

* `GET /items/filters/[type-id].ws` lists filter types for the given type.
* `POST /items/filters/[type-id].ws` creates a filter type for the given item type.
* `GET /items/filters/[type-id]/[filter-type-id].ws` lists filters of the given type.
* `POST /items/filters/[type-id]/[filter-type-id].ws` creates a filter within the given filter type.
* `PUT /items/filters/[type-id]/[filter-type-id].ws` updates the filter type with the given ID.
* `DELETE /items/filters/[type-id]/[filter-type-id].ws` deletes the filter type with the given ID.
* `GET /items/filters/[type-id]/[filter-type-id]/[filter-id].ws` lists items that are assigned to the given filter.
* `PUT /items/filters/[type-id]/[filter-type-id]/[filter-id].ws` updates the list of assigned items for the given filter.
* `DELETE /items/filters/[type-id]/[filter-type-id]/[filter-id].ws` deletes the filter with the given ID.

Filters can also be configured within categories. To do this, use any of the above URIs but replace `/items/filters/[type-id]` with `/collections/filters/[collection-id]`.

## Details

### List filter types
```
GET /items/filters/5.ws
```
```json
{
    "types": [
        {
            "id": 1,
            "name": "Colour"
        },
        {
            "id": 2,
            "name": "Brand"
        }
    ]
}
```

### Create a filter type
```
POST /items/filters/5.ws
```
This will create a new filter type from the parameters passed:
```json
{
    "name": "Size"
}
```
You'll receive a `201 Created` header, along with an `X-ResourceId` and `Location` containing a URL to find the new filter type via the API.

### List filters for a particular filter type
```
GET /items/filters/5/1.ws
```
```json
{
    "filters": [
        {
            "conditionalFilters": [],
            "id": 1,
            "name": "Red"
        },
        {
            "conditionalFilters": [],
            "id": 2,
            "name": "Green"
        },
        {
            "conditionalFilters": [],
            "id": 3,
            "name": "Blue"
        }
    ],
    "id": 1,
    "name": "Colour"
}
```

### Create a filter within a particular filter type
```
POST /items/filters/5/3.ws
```
This will create a new filter from the parameters passed:
```json
{
    "name": "Small"
}
```
You'll receive a `201 Created` header, along with an `X-ResourceId` and `Location` containing a URL to find the new filter via the API.

### Update a filter type
```
PUT /items/filters/5/3.ws
```
This will update the particular filter type based on the parameters passed:
```json

```

### List items that are assigned to a particular filter
```
GET /items/filters/5/1/2.ws
```
```json
{
    "conditionalFilters": [],
    "id": 2,
    "items": [
        {
            "id": 9
        },
        {
            "id": 11
        }
    ],
    "name": "Green"
}
```
