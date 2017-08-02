---
title: The FA API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - typescript

toc_footers:
   - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Please note all of the endpoints/responses are open to change.

```typescript
interface ItemsResponse {
  results: string[];
}
```

# Users

## Get a Specific User

```typescript
http.get<ItemsResponse>('https://api.thefa.biz/v1/users/1').subscribe(data => {
  this.results = data.results;
});
```

> The above command returns JSON structured like this:

```json
{
  "data": [
     {
       "id": 1,
       "name": "John Doe",
       "email": "john.doe@aptsolutions.net",
       "username": "johndoe99",
       "date_of_birth": "1999-05-13T00:00:00,000000000Z",
       "gender": "Male",
       "primary_team": 1
     }
  ]
}
```

This endpoint retrieves all users.

### HTTP Request

`GET https://api.thefa.biz/v1/users/<ID>`

### Query Parameters

Parameter | Description
--------- | ----------
ID | The ID of the user to retrieve

## Get Multiple Users

```typescript
http.get<ItemsResponse>('https://api.thefa.biz/v1/users/1,2,3').subscribe(data => {
  this.results = data.results;
});
```

> The above command returns JSON structured like this:

```json
{
    "data": [
        {
            "id": 1,
            "name": "John Doe",
            "email": "john.doe@test.net",
            "username": "johndoe99",
            "date_of_birth": "1999-05-13T00:00:00,000000000Z",
            "gender": "Male"
        },
        {
            "id": 2,
            "name": "Paul Smith",
            "email": "paul.smith@hotmail.com",
            "username": "psmith",
            "date_of_birth": "1999-05-13T00:00:00,000000000Z",
            "gender": "Male" 
        },
        {
            "id": 3,
            "name": "Jane Doe",
            "email": "jane.doe@test.net",
            "username": "jonedoe99",
            "date_of_birth": "1999-05-13T00:00:00,000000000Z",
            "gender": "Female" 
        }
    ]
}
```

This endpoint retrieves multiple users

### HTTP Request

`GET https://api.thefa.biz/v1/users/<ID>,<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to retrieve

# Arguments

## Get all Arguments

```typescript
http.get<ItemsResponse>('https://api.thefa.biz/v1/arguments').subscribe(data => {
  this.results = data.results;
});
```

> The above command returns JSON structured like this:

```json
{
  "data": [
     {
        "id": 1,
        "title": "Lorem Ipsum",
        "summary": "Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.",
        "content": "<h1>HTML Ipsum Presents</h1><p><strong>Pellentesque habitant morbi tristique</strong> senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. <em>Aenean ultricies mi vitae est.</em> Mauris placerat eleifend leo. Quisque sit amet est et sapien ullamcorper pharetra. Vestibulum erat wisi, condimentum sed, <code>commodo vitae</code>, ornare sit amet, wisi. Aenean fermentum, elit eget tincidunt condimentum, eros ipsum rutrum orci, sagittis tempus lacus enim ac dui. <a href=\"#\">Donec non enim</a> in turpis pulvinar facilisis. Ut felis.</p><h2>Header Level 2</h2>",
        "comment_count": 59,
        "like_count": 100,
        "publish_date": "2017-03-13T12:30:45,123456789Z",
        "expiry_date": "2017-05-13T12:30:45,123456789Z",
        "_links": {
           "authors": 1
        }
     },
     {
        "id": 2,
        "title": "Lorem Ipsum 2",
        "summary": "Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.",
        "content": "<h1>HTML Ipsum Presents</h1><p><strong>Pellentesque habitant morbi tristique</strong> senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. <em>Aenean ultricies mi vitae est.</em> Mauris placerat eleifend leo. Quisque sit amet est et sapien ullamcorper pharetra. Vestibulum erat wisi, condimentum sed, <code>commodo vitae</code>, ornare sit amet, wisi. Aenean fermentum, elit eget tincidunt condimentum, eros ipsum rutrum orci, sagittis tempus lacus enim ac dui. <a href=\"#\">Donec non enim</a> in turpis pulvinar facilisis. Ut felis.</p><h2>Header Level 2</h2>"
        "author": 1,
        "comment_count": 10,
        "like_count": 20,
        "publish_date": "2017-03-13T12:30:45,123456789Z",
        "expiry_date": "2036-05-13T12:30:45,123456789Z",
        "_links": {
           "authors": 1
        }
     }
  ],
  "_linked": {
     "authors": [
        {
           "id": 1,
           "name": "John Doe",
           "username": "johndoe99"
        } 
     ]
  },
  "pagination": {
     "total": 1000,
     "count": 12,
     "per_page": 12,
     "current_page": 1,
     "total_pages": 84
  }
}
```

This endpoint retrieves all arguments.

### HTTP Request

`GET https://api.thefa.biz/v1/arguments`

<aside class="info">
    All dates in the API conform to ISO-8601 Standards
</aside>

### Query Parameters

Parameter | default | Description
--------- | ----------- | -----------
page | 1 | The page data wanted
items | 12 | number of items per page

## Get a specific argument

```typescript
http.get<ItemsResponse>('https://api.thefa.biz/v1/arguments/2').subscribe(data => {
  this.results = data.results;
});
```

> The above command returns JSON structured like this:

```json
{
  "data": [
     {
        "id": 1,
        "title": "Lorem Ipsum",
        "summary": "Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.",
        "content": "<h1>HTML Ipsum Presents</h1><p><strong>Pellentesque habitant morbi tristique</strong> senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. <em>Aenean ultricies mi vitae est.</em> Mauris placerat eleifend leo. Quisque sit amet est et sapien ullamcorper pharetra. Vestibulum erat wisi, condimentum sed, <code>commodo vitae</code>, ornare sit amet, wisi. Aenean fermentum, elit eget tincidunt condimentum, eros ipsum rutrum orci, sagittis tempus lacus enim ac dui. <a href=\"#\">Donec non enim</a> in turpis pulvinar facilisis. Ut felis.</p><h2>Header Level 2</h2>",
        "comment_count": 59,
        "like_count": 100,
        "_links": {
           "authors": 1 
        },
        "comments": {
           "data": [
              {
                 "id": 10,
                 "comment": "lorem Ipsum! :)",
                 "created_at": "2017-03-13T12:30:45,123456789Z",
                 "like_count": 100,
                 "dislike_count": 900,
                 "_links": {
                    "authors": 2
                 }
              },
              {
                 "id": 10,
                 "comment": "lorem Ipsum! :)",
                 "created_at": "2017-03-13T12:30:45,123456789Z",
                 "like_count": 100,
                 "dislike_count": 900,
                 "_links": {
                    "authors": 1
                 }
              }
           ]
        },
        "publish_date": "2017-03-13T12:30:45,123456789Z",
        "expiry_date": "2017-05-13T12:30:45,123456789Z"
     }
  ],
  "_linked": {
     "authors": [
        {
           "id": 1,
           "name": "John Doe",
           "username": "johndoe99"
        },
        {
           "id": 3,
           "name": "Jane Doe",
           "username": "janedoe99"
        } 
     ]
  }
}
```

This endpoint retrieves all arguments.

### HTTP Request

`GET https://api.thefa.biz/v1/arguments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | ID of the argument to load

### Query Parameters

Parameter | default | Description
--------- | ----------- | -----------
include_comments | true | preload the first page of comments

## Get Comments Related to a Argument

```typescript
http.get<ItemsResponse>('https://api.thefa.biz/v1/arguments/2/comments').subscribe(data => {
  this.results = data.results;
});
```

> The above command returns JSON structured like this:

```json
{
  "data": [
     {   
         "id": 10,
         "comment": "lorem Ipsum! :)",
         "created_at": "2017-03-13T12:30:45,123456789Z",
         "like_count": 100,
         "dislike_count": 900,
         "_links": {
            "authors": 2
         }
     },
     {
         "id": 10,
         "comment": "lorem Ipsum! :)",
         "created_at": "2017-03-13T12:30:45,123456789Z",
         "like_count": 100,
         "dislike_count": 900,
         "_links": {
            "authors": 1
         }
     }
  ],
  "_linked": {
     "authors": [
        {
           "id": 1,
           "name": "John Doe",
           "username": "johndoe99"
        },
        {
           "id": 3,
           "name": "Jane Doe",
           "username": "janedoe99"
        } 
     ]
  },
  "pagination": {
     "total": 1000,
     "count": 12,
     "per_page": 12,
     "current_page": 1,
     "total_pages": 84
  }
}
```

This endpoint retrieves all comments on a argument; paginated.

### HTTP Request

`GET https://api.thefa.biz/v1/arguments/<ID>/comments`

### Query Parameters

Parameter | default | Description
--------- | ----------- | -----------
page | 1 | The page data wanted
items | 12 | number of items per page