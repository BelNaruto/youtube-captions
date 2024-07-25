# YouTube Captions API

The **YouTube Captions API** provides seamless access to YouTube video captions, enabling developers to integrate caption data into their applications and services. This API is ideal for enhancing accessibility, improving content analysis, and supporting language learning tools by leveraging YouTube's extensive caption resources. This API can be found on RapidAPI: [YouTube Captions API](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/youtube-captions).

### How to Extract the `videoId` from YouTube URLs

When using our API to add a video, you need to provide the `videoId`. The `videoId` is a unique identifier for each YouTube video. Here’s how you can find the `videoId` from different YouTube URL formats.

#### Example URL
`https://www.youtube.com/watch?v=ABE3A24KIAw`
- The `videoId` is `ABE3A24KIAw`.

### Common YouTube URL Formats

1. **Standard YouTube URL**
   - URL: `https://www.youtube.com/watch?v=ABE3A24KIAw`
   - `videoId`: The part after `v=`, which is `ABE3A24KIAw`.

2. **Shortened YouTube URL**
   - URL: `https://youtu.be/ABE3A24KIAw`
   - `videoId`: The part after `youtu.be/`, which is `ABE3A24KIAw`.

3. **YouTube URL with Additional Parameters**
   - URL: `https://www.youtube.com/watch?v=ABE3A24KIAw&t=30s`
   - `videoId`: The part after `v=`, which is `ABE3A24KIAw` (ignore other parameters like `t=30s`).

### Summarizing...

Whenever you have a YouTube URL, look for the part that starts with `v=` or comes after `youtu.be/`. That segment is the `videoId` you need to provide to our API.

**Example:**
If you have the URL `https://www.youtube.com/watch?v=ABE3A24KIAw`, you would provide `ABE3A24KIAw` as the `videoId`.

This `videoId` helps our API recognize which video you are referring to.


## Getting Started

1. **Sign Up**: Create an account on RapidAPI.
2. **Subscribe**: Choose a subscription plan that fits your needs.
3. **API Key**: Obtain your unique API key to start making requests.
4. **Documentation**: For detailed usage instructions, visit the [YouTube Captions API Documentation](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/youtube-captions).


## Route: `GET /transcript`

This route handles GET requests to retrieve the transcript of a video based on its video ID.

### Request
- **Method:** `GET`
- **URL:** `/transcript`
- **Query Parameters:**
  - `videoId` (required): The ID of the video for which the transcript is requested.

### Response
- **Status Code:** `200 OK` (on success), `500 Internal Server Error` (on server error)
- **Content-Type:** `application/json`
- **Body:**
  - On success:
    ```json
    {
        /* Transcript data for the specified video */
    }
    ```
  - On error:
    - Server error:
      ```json
      {
          "error": "Something went wrong please try again later!"
      }
      ```

### Example Usage
```javascript
fetch('/transcript?videoId=abc123')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console
```

## Route: `GET /onlycaption`

This route handles GET requests to retrieve the captions of a video based on its video ID.

### Request
- **Method:** `GET`
- **URL:** `/onlycaption`
- **Query Parameters:**
  - `videoId` (required): The ID of the video for which the captions are requested.

### Response
- **Status Code:** `200 OK` (on success), `400 Bad Request` (on missing query parameter), `404 Not Found` (on captions not found), `500 Internal Server Error` (on server error)
- **Content-Type:** `application/json`
- **Body:**
  - On success:
    ```json
    {
        /* Captions data for the specified video */
    }
    ```
  - On error:
    - Missing videoId:
      ```json
      {
          "message": "Please provide the videoId"
      }
      ```
    - Captions not found:
      ```json
      {
          "error": "Captions not found for this video!"
      }
      ```
    - Server error:
      ```json
      {
          "error": "Something went wrong! Check if this video has captions on YouTube"
      }
      ```

### Example Usage
```javascript
fetch('/onlycaption?videoId=abc123')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```

## Route: `GET /onlycaption/translation`

This route handles GET requests to retrieve translated captions of a video based on its video ID and target language.

### Request
- **Method:** `GET`
- **URL:** `/onlycaption/translation`
- **Query Parameters:**
  - `videoId` (required): The ID of the video for which the captions are requested.
  - `targetLanguage` (optional, default: `'pt'`): The target language for the translation of the captions.

### Response
- **Status Code:** `200 OK` (on success), `400 Bad Request` (on missing query parameters), `404 Not Found` (on captions not found), `500 Internal Server Error` (on server error)
- **Content-Type:** `application/json`
- **Body:**
  - On success:
    ```json
    {
        "data": {
            /* Translated captions data for the specified video */
        }
    }
    ```
  - On error:
    - Missing videoId:
      ```json
      {
          "message": "Please provide the videoId"
      }
      ```
    - Missing targetLanguage:
      ```json
      {
          "message": "Please provide the targetLanguage"

## Route: `GET /caption/translation`

This route handles GET requests to retrieve translated captions of a video based on its video ID and target language.

### Request
- **Method:** `GET`
- **URL:** `/caption/translation`
- **Query Parameters:**
  - `videoId` (required): The ID of the video for which the captions are requested.
  - `targetLanguage` (optional, default: `'es'`): The target language for the translation of the captions.

### Response
- **Status Code:** `200 OK` (on success), `400 Bad Request` (on missing query parameters), `500 Internal Server Error` (on server error)
- **Content-Type:** `application/json`
- **Body:**
  - On success:
    ```json
    {
        "data": {
            /* Translated captions data for the specified video */
        }
    }
    ```
  - On error:
    - Missing videoId:
      ```json
      {
          "message": "Please provide the videoId"
      }
      ```
    - Missing targetLanguage:
      ```json
      {
          "message": "Please provide the targetLanguage"
      }
      ```
    - Server error:
      ```json
      {
          "error": "Something went wrong! Check if this video has captions on YouTube"
      }
      ```

### Example Usage
```javascript
fetch('/caption/translation?videoId=abc123&targetLanguage=fr')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));

```
## Route: `GET /transcript2`

This route handles GET requests to retrieve the transcript of a video based on its video ID.

### Request
- **Method:** `GET`
- **URL:** `/transcript2`
- **Query Parameters:**
  - `videoId` (required): The ID of the video for which the transcript is requested.

### Response
- **Status Code:** `200 OK` (on success), `400 Bad Request` (on missing query parameters), `404 Not Found` (on captions not found), `500 Internal Server Error` (on server error)
- **Content-Type:** `application/json`
- **Body:**
  - On success:
    ```json
    {
        /* Transcript data for the specified video */
    }
    ```
  - On error:
    - Missing videoId:
      ```json
      {
          "message": "Please provide the videoId"
      }
      ```
    - Captions not found:
      ```json
      {
          "error": "Captions not found for this video!"
      }
      ```
    - Server error:
      ```json
      {
          "error": "Something went wrong! Check if this video has captions on YouTube"
      }
      ```

### Example Usage
```javascript
fetch('/transcript2?videoId=abc123')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```
## Route: `GET /transcript3`

This route handles GET requests to retrieve the transcript of a video based on its video ID.

### Request
- **Method:** `GET`
- **URL:** `/transcript3`
- **Query Parameters:**
  - `videoId` (required): The ID of the video for which the transcript is requested.

### Response
- **Status Code:** `200 OK` (on success), `400 Bad Request` (on missing query parameters), `404 Not Found` (on captions not found), `500 Internal Server Error` (on server error)
- **Content-Type:** `application/json`
- **Body:**
  - On success:
    ```json
    {
        /* Transcript data for the specified video */
    }
    ```
  - On error:
    - Missing videoId:
      ```json
      {
          "message": "Please provide the videoId"
      }
      ```
    - Captions not found:
      ```json
      {
          "error": "Captions not found for this video!"
      }
      ```
    - Server error:
      ```json
      {
          "error": "Something went wrong! Check if this video has captions on YouTube"
      }
      ```

### Example Usage
```javascript
fetch('/transcript3?videoId=abc123')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));


## Commonly Asked Questions

### 1. What kind of data can I access through the YouTube Captions API?
You can access captions for YouTube videos, including caption text, metadata, and timestamp information.

### 2. How do I authenticate my API requests?
You need to include your API key in the headers of your requests as specified in the API documentation.

### 3. Are there usage limits for the API?
Yes, usage limits depend on the subscription plan you select. Check the RapidAPI dashboard for details.

### 4. Can I retrieve captions in different languages?
Yes, the API supports accessing captions in various languages, depending on the availability of captions for the video.

### 5. Can I download captions for offline use?
Yes, you can download caption files in different formats for offline use or further processing.

### 6. How frequently is the caption data updated?
The caption data is updated based on the availability and updates made by the video uploader on YouTube.

### 7. Can I search for captions by video ID?
Yes, you can easily find and retrieve captions for specific YouTube videos using their unique video IDs.

### 8. What formats does the API support for caption data?
The API supports various formats for caption data, making it easy to integrate into different applications and services.

### 9. Are there specific endpoints for different types of caption data (e.g., metadata, text)?
Yes, the API includes specific endpoints for various types of caption data, such as caption text and metadata.

### 10. How can I stay updated on changes to the API?
You can stay informed about updates and changes by checking the API documentation and RapidAPI dashboard regularly.

For more information and to start using the YouTube Captions API, visit [YouTube Captions API on RapidAPI](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/youtube-captions).
