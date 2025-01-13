<template>
  <div id="app">
    <h1>Weather App</h1>
    <input v-model="city" placeholder="Enter city name" @keyup.enter="getWeather" />
    <button @click="getWeather">Search</button>
    <WeatherCard v-if="weatherData" :weather="weatherData" />
  </div>
</template>

<script>
import WeatherCard from './components/WeatherCard.vue';

export default {
  components: {
    WeatherCard,
  },
  data() {
    return {
      city: '',
      weatherData: null,
      apiKey: 'd4495be6433b17d605fa1512efabfd08', // Replace with your OpenWeatherMap API key
    };
  },
  methods: {
    async getWeather() {
      if (this.city.trim()) {
        const response = await fetch(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=${this.apiKey}`
        );
        this.weatherData = await response.json();
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}
input {
  padding: 8px;
  margin-right: 8px;
}
button {
  padding: 8px 16px;
  cursor: pointer;
}
</style>
