# Smart Fuel Navigation

![Smart Fuel Navigation Demo](https://img.shields.io/badge/Status-Active-brightgreen)  
A cutting-edge web application that revolutionizes navigation by integrating real-time fuel tracking, intelligent route planning, and voice-assisted guidance. Built with Leaflet, Leaflet Routing Machine, and OpenStreetMap APIs, this project ensures drivers never run out of fuel while optimizing their journeys across India.

## Table of Contents
- [Features](#features)
- [Demo](#demo)
- [Installation](#installation)
- [Usage](#usage)
- [Technologies](#technologies)
- [File Structure](#file-structure)
- [How It Works](#how-it-works)
- [Contributing](#contributing)
- [License](#license)

## Features
- **Real-Time Fuel Tracking**: Monitor current fuel levels and estimate maximum travel distance based on vehicle efficiency (15 km/liter).
- **Smart Route Planning**: Uses Leaflet Routing Machine with OSRM for precise navigation from user location to destination.
- **Low Fuel Alerts**: Proactive notifications when fuel drops below 10% of tank capacity (50 liters).
- **Nearest Petrol Station Finder**: Leverages Overpass API to locate nearby fuel stations within a 5 km radius.
- **Voice Assistance**: Provides audio guidance for routes, fuel alerts, and navigation updates (English, Indian accent).
- **Interactive Map Interface**: Powered by Leaflet and OpenStreetMap for a seamless mapping experience.
- **Fuel Simulation**: Simulate fuel consumption for a 50 km journey to test low-fuel scenarios.
- **Responsive Design**: Optimized for both desktop and mobile devices.

## Demo
Try the live demo [here](https://tsreddy1130.github.io/smart_fuel_Maps/) .  
*Note*: Ensure location access is enabled for full functionality.

## Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Tsreddy1130/smart_fuel_Maps.git
   cd smart-fuel-navigation
   ```

2. **Serve the Application**:
   - No dependencies are required as all libraries are loaded via CDN.
   - Use a local server (e.g., Python's HTTP server or VS Code's Live Server):
     ```bash
     python -m http.server 8000
     ```
   - Open `http://localhost:8000` in your browser.

3. **Grant Location Access**:
   - The app requires geolocation to function correctly. Allow location access when prompted.

## Usage
1. **Enter Destination**:
   - Input a destination in India (e.g., "Taj Mahal") in the search bar and click "Navigate".
   - The app uses Nominatim API to geocode the destination and plots the route.

2. **Monitor Fuel**:
   - Update the "Current Fuel" input (in liters) to reflect your vehicle's fuel level.
   - Click "Simulate Fuel Use" to deduct 3.33 liters (equivalent to 50 km travel).

3. **Low Fuel Alerts**:
   - If fuel falls below 5 liters (10% of 50-liter tank), the app alerts you and suggests the nearest petrol station.
   - Click the station link in the modal to reroute to it.

4. **Voice Guidance**:
   - Audio cues guide you through route updates, fuel warnings, and navigation steps.

## Technologies
- **HTML5/CSS3**: For structure and responsive styling.
- **JavaScript (ES6)**: Core logic for fuel tracking, routing, and API integration.
- **Leaflet.js**: Interactive map rendering.
- **Leaflet Routing Machine**: Route planning with OSRM backend.
- **OpenStreetMap APIs**:
  - **Nominatim**: Geocoding for destination search.
  - **Overpass API**: Petrol station lookup.
  - **OSRM**: Route calculation.
- **Web Speech API**: Voice synthesis for audio guidance.
- **CDNs**: Unpkg for Leaflet and Routing Machine libraries.

## File Structure
```
smart-fuel-navigation/
├── index.html        # Main application file
├── README.md         # Project documentation
└── assets/           # (Optional) Placeholder for images or additional files
```

## How It Works
1. **Geolocation**:
   - On load, the app requests user location via `navigator.geolocation`.
   - Centers the map on the user's coordinates and adds a marker.

2. **Fuel Tracking**:
   - Tracks fuel using a default tank capacity (50 liters) and efficiency (15 km/liter).
   - Calculates max travel distance (`fuel * efficiency`) and checks for low fuel (`< 10%` of tank).

3. **Routing**:
   - User inputs a destination, geocoded via Nominatim API.
   - Leaflet Routing Machine plots the route using OSRM, displaying distance and time.
   - Fuel feasibility is checked by comparing route distance to max travel distance.

4. **Petrol Station Detection**:
   - If fuel is insufficient or low, Overpass API queries for nearby fuel stations (`amenity=fuel`).
   - The nearest station is calculated using the Haversine formula and displayed in a modal.

5. **Voice Feedback**:
   - Web Speech API (`SpeechSynthesisUtterance`) provides audio updates with `en-IN` language setting.

## Contributing
We welcome contributions! Follow these steps:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/YourFeature`).
3. Commit changes (`git commit -m "Add YourFeature"`).
4. Push to the branch (`git push origin feature/YourFeature`).
5. Open a Pull Request.

Please adhere to the [Code of Conduct](CODE_OF_CONDUCT.md) and ensure code is well-documented.

