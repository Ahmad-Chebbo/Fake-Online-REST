# Getting Started

Rapidly develop User Interfaces with fake APIs.

Back-end not ready or just want to prototype something?
Describe your data, automatically get a fake REST & GraphQL API with random values.

## Config

For a quick start, create a new `.mockend.json` at the root of your repository:

```json
{
  "Post": {
    "title": { "string": {} },
    "comments": {
      "hasMany": "Comment"
    }
  },
  "Comment": {
    "body": { "string": {} },
    "post": {
      "belongsTo": "Post"
    }
  }
}
```

*Many types (string, int, boolean, dateTime) and custom values are supported, see configuration for a complete list of options.*

You can visit https://mockend.com/org/repo/posts or https://mockend.com/org/repo/graphql to confirm that everything's working.

## REST

Based on the previous config, the following API will be automatically created:

```
GET https://mockend.com/Ahmad-Chebbo/Fake-Online-REST/posts
GET https://mockend.com/Ahmad-Chebbo/Fake-Online-REST/posts/<id>
GET https://mockend.com/Ahmad-Chebbo/Fake-Online-REST/comments
GET https://mockend.com/Ahmad-Chebbo/Fake-Online-REST/comments/<id>
```

Query parameters can be used to filter, sort and paginate lists:

* `_eq` `_ne` equal, not equal
* `_gt` `_lt` greater than, lower than
* `_order=asc|desc` sort data
* limit offset paginate results

For example, to get posts ordered by creation date:
```
GET /posts?createdAt_order=desc
```
Or the top five most viewed posts:

```
GET /posts?limit=5&views_order=desc
```

Or published posts with less than 100 views:

```
GET /posts?published_eq=true&views_lt=100
```

For more information visit: **[Mockend](https://docs.mockend.com/config)**
