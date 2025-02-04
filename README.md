# MoviesDatabase API

## API Overview

- [moviesdatabase API docs](https://rapidapi.com/SAdrian/api/moviesdatabase)

moviesdatabase API provides collection of information for movies, tv-shows, actors. Includes youtube trailer url, awards, full biography, and many other usefull informations. This api provides complete and updated data for over 9 million titles ( movies, series and episodes) and 11 million actors / crew and cast members.

## Version

**API Version:** 1.0

## Available Endpoints

- **Prefix**: **https://moviesdatabase.p.rapidapi.com**

### Titles

- **GET /titles** : returns array of titles according to filters / sorting query parameters provided
- **GET /x/titles-by-ids** : returns array of titles according to array of id's provided
- **GET /titles/{id} parameter id:(required) imdb id of title** : returns title acording to filters / sorting query parameters provided

### Actors

- **GET /actors** : returns array of actors according to filters
- **GET /actors/{id} parameter id:(required) imdb id of actor** : returns actor details

### Utils

- **GET /title/utils/titleType** : returns array of title types
- **GET /title/utils/genres** : returns array of genres
- **GET /title/utils/lists** : returns array of lists (for 'list' query parameter)

### Obsolete

- **GET /title/{id}crew** : returns crew memebers of the provided title
- **GET /title/{id}/main_actors** : returns main actors of the provided title

## Request and Response Format

### Request Example

**GET https://moviesdatabase.p.rapidapi.com/titles**

```javascript
const options = {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'moviesdatabase.p.rapidapi.com',
    'x-rapidapi-key': `${API_KEY}`,
  },
};

fetch(
  'https://moviesdatabase.p.rapidapi.com/titles?page=2&limit=12&year=2025&sort=year.decr',{options}
)
  .then((res) => res.json())
  .then((res) => console.log(res))
  .catch((err) => console.error(err));
```

### Response Example

**Success Response:**

```json
{
  "page": "1",
  "next": "/titles?page=2&limit=12&year=2025&sort=year.decr",
  "entries": 12,
  "results": [
    {
      "_id": "61e58b91d735dff3f943afb9",
      "id": "tt10064424",
      "primaryImage": "[Object]",
      "titleType": "[Object]",
      "titleText": "[Object]",
      "originalTitleText": "[Object]",
      "releaseYear": "[Object]",
      "releaseDate": "[Object]"
    }
  ]
}
```

**Error Response:**

```json
{
  "message": "Invalid API key. Go to https://docs.rapidapi.com/docs/keys for more info."
}
```

## Authentication

To authenticate your requests, include your API key in the request header as follows:

**Header Example:**

```javascript
 headers: {
          'x-rapidapi-host': 'moviesdatabase.p.rapidapi.com',
          'x-rapidapi-key': `${API_KEY}`,
        },
```

You can obtain an API key by signing up on the developer portal.

## Error Handling

Common error responses include:

- **401 Unauthorized:** Invalid API key.
- **404 Not Found:** The resource requested could not be found.
- **429 Too Many Requests:** Rate limit exceeded.

Handle errors by checking the response status and logging the error message. For example:

```javascript
if (!response.ok) {
  console.error(`Error: ${response.status} - ${response.statusText}`);
}
```

## Usage Limits and Best Practices

### Usage Limits

- **Rate Limit:** 1000 requests per hour(on free(basic) tier). 5 requests per second(on pro tier) .

### Best Practices

- Use caching to reduce redundant API requests.
- Handle errors gracefully and implement retry logic for transient issues.
- Respect the rate limits to avoid being throttled.
- Paginate results when fetching large datasets.

---
