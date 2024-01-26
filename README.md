import React, { useState, useEffect } from 'react';
import axios from 'axios';

const WeatherDisplay = ({ location }) => {
  const [weatherData, setWeatherData] = useState(null);

  useEffect(() => {
    const apiKey = 'YOUR_API_KEY';
    const apiUrl = `https://api.openweathermap.org/data/2.5/forecast?q=${location}&appid=${apiKey}`;

    axios.get(apiUrl)
      .then(response => setWeatherData(response.data))
      .catch(error => console.error('Error fetching weather data:', error));
  }, [location]);

  // Render weather information based on weatherData

  return (
    <div>
      {/* Display weather information here */}
    </div>
  );
};

export default WeatherDisplay;
//Auto detenction
// Inside your App component
useEffect(() => {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(
      (position) => {
        // Update state with user's current location
      },
      (error) => {
        console.error('Error getting location:', error);
      }
    );
  } else {
    console.error('Geolocation is not supported by your browser');
  }
}, []);
