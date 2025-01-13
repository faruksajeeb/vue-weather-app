<template>
    <div v-if="weather" class="weather-card">
      <h2>{{ weather.name }}</h2>
      <p>{{ weather.weather[0].description }}</p>
      <p>Temperature: {{ weather.main.temp }}°C</p>
      <p>Humidity: {{ weather.main.humidity }}%</p>
      <p>Wind Speed: {{ weather.wind.speed }} m/s</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      weather: Object,
    },
  };
  </script>
  
  <style scoped>
  .weather-card {
    border: 1px solid #ddd;
    padding: 16px;
    border-radius: 8px;
    max-width: 300px;
    margin: 0 auto;
    text-align: center;
  }
  </style>
  