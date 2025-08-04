# alx-project-0x14

## API Overview

The MoviesDatabase API is a comprehensive movie database service that provides access to a vast collection of movie information, including titles, release years, genres, and poster images. This API allows developers to build applications that can search, filter, and display movie data with rich metadata.

## Version

The current version of the MoviesDatabase API is v1.0

## Available Endpoints

### 1. Titles Endpoint
- **URL**: `https://moviesdatabase.p.rapidapi.com/titles`
- **Method**: GET
- **Description**: Retrieves a list of movie titles with filtering options
- **Parameters**:
  - `year`: Filter movies by release year
  - `sort`: Sort order (e.g., `year.decr` for descending year)
  - `limit`: Number of results per page (default: 12)
  - `page`: Page number for pagination
  - `genre`: Filter by movie genre

### 2. Title Details Endpoint
- **URL**: `https://moviesdatabase.p.rapidapi.com/titles/{id}`
- **Method**: GET
- **Description**: Retrieves detailed information about a specific movie
- **Parameters**:
  - `id`: Unique identifier for the movie

### 3. Search Endpoint
- **URL**: `https://moviesdatabase.p.rapidapi.com/titles/search/title/{title}`
- **Method**: GET
- **Description**: Searches for movies by title
- **Parameters**:
  - `title`: Movie title to search for

## Request and Response Format

### Request Format
```json
{
  "year": 2024,
  "page": 1,
  "genre": "Action",
  "limit": 12
}
```

### Response Format
```json
{
  "results": [
    {
      "id": "tt1234567",
      "primaryImage": {
        "url": "https://example.com/poster.jpg"
      },
      "titleText": {
        "text": "Movie Title"
      },
      "releaseYear": {
        "year": "2024"
      }
    }
  ],
  "total": 1000,
  "page": 1,
  "limit": 12
}
```

## Authentication

The MoviesDatabase API requires authentication using RapidAPI:

1. **API Key**: Obtain an API key from RapidAPI
2. **Headers Required**:
   - `x-rapidapi-host`: `moviesdatabase.p.rapidapi.com`
   - `x-rapidapi-key`: Your RapidAPI key

### Example Request Headers
```javascript
{
  "x-rapidapi-host": "moviesdatabase.p.rapidapi.com",
  "x-rapidapi-key": "YOUR_API_KEY_HERE"
}
```

## Error Handling

### Common Error Responses

1. **401 Unauthorized**
   - **Cause**: Invalid or missing API key
   - **Solution**: Verify your API key is correct and included in headers

2. **429 Too Many Requests**
   - **Cause**: Rate limit exceeded
   - **Solution**: Implement exponential backoff and respect rate limits

3. **400 Bad Request**
   - **Cause**: Invalid parameters or malformed request
   - **Solution**: Check request parameters and format

4. **500 Internal Server Error**
   - **Cause**: Server-side error
   - **Solution**: Retry request after a delay

### Error Response Format
```json
{
  "error": {
    "message": "Error description",
    "code": "ERROR_CODE"
  }
}
```

## Usage Limits and Best Practices

### Rate Limits
- **Free Tier**: 100 requests per day
- **Paid Tiers**: Varies by subscription plan
- **Rate Limit Headers**: Check `X-RateLimit-*` headers for current usage

### Best Practices

1. **Caching**: Implement caching for frequently requested data
2. **Pagination**: Use pagination to handle large result sets
3. **Error Handling**: Implement proper error handling and retry logic
4. **Request Optimization**: Only request necessary fields to reduce response size
5. **Rate Limiting**: Respect API rate limits and implement backoff strategies

### Performance Tips
- Use appropriate `limit` values to optimize response times
- Implement client-side caching for static data
- Use filtering parameters to reduce unnecessary data transfer
- Monitor API usage to stay within rate limits

### Security Considerations
- Never expose API keys in client-side code
- Use environment variables for API key storage
- Implement proper CORS policies
- Validate and sanitize all user inputs before making API requests