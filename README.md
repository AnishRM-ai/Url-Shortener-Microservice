# URL Shortener Microservice

A lightweight microservice built with Node.js that converts long URLs into short, manageable links. This API-based service provides a simple and efficient way to create shortened URLs that redirect to their original destinations.

## What It Does

This microservice accepts long URLs via API endpoints and generates shortened versions that are easier to share and remember. When users visit the shortened URL, they are automatically redirected to the original link. The service validates URLs to ensure they follow proper formatting and stores mappings between short and original URLs.

## Features

### Core Functionality

- **URL Shortening**
  - POST long URLs to receive shortened versions
  - Automatic generation of unique short URL identifiers
  - JSON response with both original and shortened URLs
  - URL validation to ensure proper formatting

- **URL Redirection**
  - Visit shortened URLs to redirect to original links
  - Fast lookup and redirection
  - Persistent URL mappings

- **API Endpoints**
  - RESTful API design
  - POST endpoint for creating shortened URLs
  - GET endpoint for redirection
  - Error handling for invalid URLs

- **URL Validation**
  - Validates URLs follow http(s)://www.example.com format
  - Returns error messages for invalid URLs
  - Ensures URLs point to valid sites

## Tech Stack

- **Runtime:** Node.js
- **Framework:** Express.js (likely)
- **Language:** JavaScript
- **API:** RESTful architecture

## Project Structure

```
Url-Shortener-Microservice/
├── index.js              # Main application file
├── package.json          # Dependencies and scripts
├── package-lock.json     # Dependency lock file
├── .gitignore           # Git ignore rules
└── README.md            # Project documentation
```

## Installation & Setup

### Prerequisites

- Node.js (v12 or higher)
- npm (Node Package Manager)

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/AnishRM-ai/Url-Shortener-Microservice.git
   cd Url-Shortener-Microservice
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the server**
   ```bash
   npm start
   ```
   Or:
   ```bash
   node index.js
   ```

4. **Access the service**
   - The service will typically run on `http://localhost:3000`
   - API endpoint: `http://localhost:3000/api/shorturl`

## API Usage

### Create a Shortened URL

**Endpoint:** `POST /api/shorturl/new`

**Request Body:**
```json
{
  "url": "https://www.example.com/very/long/url/path"
}
```

**Response:**
```json
{
  "original_url": "https://www.example.com/very/long/url/path",
  "short_url": 1
}
```

### Invalid URL Response

**Request:**
```json
{
  "url": "invalid-url-format"
}
```

**Response:**
```json
{
  "error": "invalid URL"
}
```

### Access Shortened URL

**Endpoint:** `GET /api/shorturl/:short_url`

**Example:** `GET /api/shorturl/1`

**Result:** Redirects to the original URL

## How It Works

1. User submits a long URL via POST request to `/api/shorturl/new`
2. Service validates the URL format
3. If valid, generates a unique short identifier
4. Stores the mapping between short and original URL
5. Returns JSON response with both URLs
6. When short URL is visited, service looks up original URL and redirects

## Example Usage

```javascript
// Creating a shortened URL
fetch('http://localhost:3000/api/shorturl/new', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    url: 'https://www.example.com'
  })
})
.then(response => response.json())
.then(data => console.log(data));

// Expected output:
// { original_url: 'https://www.example.com', short_url: 1 }
```

## Features in Detail

### URL Validation
- Ensures URLs follow http:// or https:// protocol
- Validates domain format (www.example.com)
- Checks for proper URL structure
- Returns descriptive error messages

### Short URL Generation
- Generates unique identifiers for each URL
- Compact format for easy sharing
- Sequential or random ID generation

### Error Handling
- Invalid URL format detection
- Duplicate URL handling
- Graceful error responses

---

**Note:** This is a personal portfolio project demonstrating microservice architecture and RESTful API development with Node.js.
