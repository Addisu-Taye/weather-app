
# Weather App

A simple weather application that allows users to get current weather information based on their location or any city of their choice. The app pulls data from a weather API and presents it in an easy-to-read format, including temperature, weather conditions, humidity, and more.

## Features

Get real-time weather data for any city.
Displays current temperature, humidity, weather condition (e.g., sunny, cloudy, rainy), and wind speed.
Uses OpenWeatherMap API to fetch weather data.
User-friendly interface with a clean and responsive design.

## Demo

(You can upload a screenshot of your app's interface here, or provide a link to a live demo if you have one.)

## Technologies Used
1. Frontend: HTML, CSS, JavaScript
2. API: OpenWeatherMap API
3. Libraries: Axios (for API requests)

## Installation

To get started with this project locally, follow these steps:

1. Clone the repository:

bash
Copy code
git clone https://github.com/addisu-taye/weather-app.git

2. Navigate to the project folder:

bash
Copy code
cd weather-app

3. Open index.html in your browser:

You can double-click index.html to open it directly in your browser, or use a local server for development.

4. (Optional) Set up your own API key:

If you'd like to get your own API key from OpenWeatherMap, you can sign up on their website and replace the placeholder API key in the JavaScript file (app.js or similar).

## Usage

Open the app in your browser.
Enter the name of a city or allow the app to fetch your current location.
The weather information for the selected city or location will be displayed.

## Contributing

1. Fork the repository.
2. Create a new branch (git checkout -b feature-name).
3. Make your changes.
4. Commit your changes (git commit -am 'Add new feature').
5. Push to the branch (git push origin feature-name).
6. Open a pull request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

OpenWeatherMap API
Inspiration and guidance from ChatGPT.

# API Reference
This weather app uses the OpenWeatherMap API to fetch real-time weather data. Below are the key API endpoints and how they are used in the app.

## Base URL
The base URL for the OpenWeatherMap API is:

https://api.openweathermap.org/data/2.5/

## Endpoints Used

## 1.  Current Weather Data
The current weather data endpoint is used to retrieve the current weather information for a specific city or geolocation (latitude and longitude).

- Endpoint: /weather
- Request Method: GET
- Required Parameters:

- q – The name of the city (e.g., London).
- appid – Your API key for authentication (e.g., YOUR_API_KEY).

## Optional Parameters:
- units – The units of measurement for temperature (e.g., metric for Celsius, imperial for Fahrenheit). Default is standard.
- lang – Language of the response (e.g., en, es).
## Example Request:

```  
http

GET https://api.openweathermap.org/data/2.5/weather?q=London&appid=YOUR_API_KEY&units=metric
Example Response:
json

{
  "weather": [
    {
      "description": "clear sky",
      "icon": "01d"
    }
  ],
  "main": {
    "temp": 20.5,
    "humidity": 60,
    "pressure": 1015
  },
  "wind": {
    "speed": 3.1
  },
  "name": "London",
  "sys": {
    "country": "GB"
  }
}

 ```
## Response Explanation:
weather[0].description: A short description of the weather (e.g., "clear sky").
main.temp: The current temperature in Celsius (e.g., 20.5°C).
main.humidity: The humidity percentage (e.g., 60%).
main.pressure: Atmospheric pressure in hPa.
wind.speed: Wind speed in meters per second.
name: Name of the city (e.g., London).
sys.country: Country code (e.g., GB for the United Kingdom).
2. Geolocation (for User Location)
To get weather data based on the user's geographical coordinates (latitude and longitude), you can use the /weather endpoint as well. This is typically used when the user allows the app to access their location.

Endpoint: /weather
Request Method: GET
Required Parameters:
lat – Latitude of the user's location.
lon – Longitude of the user's location.
appid – Your API key.
Optional Parameters:
units – The units of measurement (e.g., metric or imperial).
lang – Language of the response (e.g., en).
Example Request:

http
Copy code
GET https://api.openweathermap.org/data/2.5/weather?lat=51.5074&lon=-0.1278&appid=YOUR_API_KEY&units=metric
Example Response:
json
Copy code
{
  "weather": [
    {
      "description": "clear sky",
      "icon": "01d"
    }
  ],
  "main": {
    "temp": 18.2,
    "humidity": 65
  },
  "wind": {
    "speed": 5.0
  },
  "name": "London",
  "sys": {
    "country": "GB"
  }
}
API Key
To make requests to the OpenWeatherMap API, you need an API key. To get your API key:

Sign up for a free account at OpenWeatherMap.
After signing in, navigate to the API Keys section of your dashboard.
Generate a new API key and copy it.
Paste the API key into your app’s configuration file or environment variables.
Rate Limiting
OpenWeatherMap imposes rate limits on how many requests you can make per minute/hour depending on your API key type (free or paid). The free tier typically allows around 60 requests per minute. Make sure to handle errors gracefully if you exceed the rate limit.

For more details on rate limits and usage policies, refer to OpenWeatherMap's documentation.

Example Code to Make an API Request in JavaScript
Here's an example of how you can use Axios (or any other HTTP client) to make a request to the OpenWeatherMap API:

javascript
Copy code
// Import Axios or use a similar HTTP client
const axios = require('axios');

const getWeather = async (city) => {
  const apiKey = 'YOUR_API_KEY';  // Replace with your API key
  const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;

  try {
    const response = await axios.get(url);
    const data = response.data;
    console.log(`Weather in ${data.name}: ${data.weather[0].description}`);
    console.log(`Temperature: ${data.main.temp}°C`);
    console.log(`Humidity: ${data.main.humidity}%`);
    console.log(`Wind Speed: ${data.wind.speed} m/s`);
  } catch (error) {
    console.error('Error fetching weather data:', error);
  }
};

// Example usage
getWeather('London');
Conclusion
This weather app relies on the OpenWeatherMap API to retrieve current weather data for any city or location. You can modify the app to support additional API endpoints like forecasts or historical data by exploring the OpenWeatherMap API documentation.