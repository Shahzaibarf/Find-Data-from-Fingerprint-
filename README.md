# Fingerprint App

This is a simple Node.js application using Express.js to upload, process, and store fingerprint images in a MongoDB database. The app also provides functionality to compare a newly scanned fingerprint with stored fingerprint data to check for matches.

## Features

- **Upload Fingerprint Images**: Users can upload fingerprint images which are processed and stored in a MongoDB database.
- **Image Processing**: The application uses OpenCV (via `opencv4nodejs`) to process the uploaded images and extract key features (e.g., contours).
- **Fingerprint Matching**: The app compares newly scanned fingerprints with stored data to check for potential matches.

## Requirements

- Node.js and npm
- MongoDB
- OpenCV (via `opencv4nodejs`)

## Installation

1. **Clone the repository**:
    ```bash
    git clone https://github.com/yourusername/fingerprint-app.git
    cd fingerprint-app
    ```

2. **Install dependencies**:
    ```bash
    npm install
    ```

3. **Ensure MongoDB is running**:
    Make sure you have MongoDB installed and running on your system.

4. **Start the server**:
    ```bash
    node server.js
    ```

5. **Access the app**:
    The server will run on `http://localhost:3000`.

## Usage

### 1. Upload a Fingerprint

- Use the provided HTML form to upload a fingerprint image.
- The image is processed, and key features are extracted.
- The extracted data is stored in the MongoDB database.

### 2. Scan and Compare a Fingerprint

- Submit a new fingerprint image to the `/scan` endpoint.
- The app will process the image and compare it to stored fingerprint data.
- If a match is found, a success message is returned.

## API Endpoints

### `/upload` [POST]

- **Description**: Upload and process a fingerprint image.
- **Request**: Multipart form-data with the file under the key `fingerprint`.
- **Response**: JSON with a success message or error.

### `/scan` [POST]

- **Description**: Compare a new fingerprint image against stored data.
- **Request**: Multipart form-data with the file under the key `fingerprint`.
- **Response**: JSON indicating whether the fingerprint matched any stored data.

## Example Usage with cURL

### Upload a Fingerprint
```bash
curl -X POST -F "fingerprint=@path/to/your/fingerprint.jpg" http://localhost:3000/upload
