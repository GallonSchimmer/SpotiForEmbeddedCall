# SpotiForEmbeddedCall, Spotify Top Tracks Web App


This simple web app uses vanilla JavaScript to make requests to the Spotify API and display the top tracks from a predefined playlist. The code includes examples of how to handle Spotify API authentication, make requests, and process responses. To run this code, make sure to host it on an Apache localhost.

## Getting Started

### Prerequisites

Before running the application, you need to have a Spotify Developer account and create an app to obtain the client ID and client secret. Visit the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/applications) to create your app.

### Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/your-username/spotify-top-tracks.git
   ```

2. Navigate to the project directory:

   ```bash
   cd spotify-top-tracks
   ```

3. Open the `index.html` file in your preferred code editor.

4. Replace the placeholder values for `clientId` and `clientSecret` with the actual values from your Spotify Developer app.

   ```javascript
   const clientId = 'your-client-id';
   const clientSecret = 'your-client-secret';
   ```

5. Save the changes to the `index.html` file.

## Usage

1. Ensure that your Apache server is running.

2. Open the `index.html` file in a web browser.

3. The web app will make a request to the Spotify API, retrieve the top tracks from the specified playlist, and display them in a table.

## Example

Here is a snippet of the JavaScript code that handles the Spotify API authentication and request:

```javascript
// Use predefined client ID and client secret
const clientId = 'your-client-id';
const clientSecret = 'your-client-secret';

// Use fetch API to get access token
fetch('https://accounts.spotify.com/api/token', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/x-www-form-urlencoded',
    },
    body: `grant_type=client_credentials&client_id=${clientId}&client_secret=${clientSecret}`
})
.then(response => response.json())
.then(data => {
    const accessToken = data.access_token;

    // Set up headers for the HTTP GET request
    const headers = {
        'Authorization': `Bearer ${accessToken}`,
        'Content-Type': 'application/json',
    };

    // Send the HTTP GET request to the Spotify API for the top tracks
    return fetch('https://api.spotify.com/v1/playlists/37i9dQZEVXbMDoHDwVN2tF/tracks?limit=10', { headers });
})
.then(response => response.json())
.then(data => {
    // Process the response and display top tracks in the table
    // ...
})
.catch(error => console.error('Error:', error));
```
