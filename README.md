Coder Finder API
A full-stack MERN application that uses geospatial querying to help users find software developers within a specific radius of their current location.

Project Features
Location-Based Search: Calculates real-time distance between the user and developers using MongoDB $geoNear.

Spherical Geometry: Uses a 2dsphere index for accurate earth-surface distance calculations.

Dynamic UI: A React-based frontend that updates results without page refreshes.

RESTful Endpoints: Full CRUD support for managing the coder database.

Installation and Setup
1. Prerequisites
Node.js installed on your machine.

MongoDB installed and running locally.

2. Clone and Install
Bash
git clone <your-repo-url>
cd coder-finder
npm install
3. Run the Application
Start the server using nodemon or node:

Bash
nodemon index
The application will be available at http://localhost:3000.

How to Use
Using the Frontend
Navigate to http://localhost:3000 in your browser.

Enter your Latitude (e.g., -1.9) and Longitude (e.g., 30.0).

Click Find Coders.

The list will display the name, rank, and distance (in km) of coders within 100km of your location.

Using the API (Postman/Insomnia)
Find Coders (GET)
URL: /api/coders?lng={longitude}&lat={latitude} Example: http://localhost:3000/api/coders?lng=30.0&lat=-1.9

Add a New Coder (POST)
URL: /api/coders Body (JSON):

JSON
{
    "name": "Jean-Luc",
    "prof": "Mobile Developer",
    "available": true,
    "geometry": {
        "type": "Point",
        "coordinates": [30.06, -1.94]
    }
}
Note: In the coordinates array, Longitude must come first (index 0) and Latitude second (index 1).

Project Structure
models/coder.js: Mongoose schema with 2dsphere indexing.

routes/api.js: Express routes for handling API requests and aggregation logic.

public/index.html: React frontend component and UI.

index.js: Main entry point for the Node.js application.
