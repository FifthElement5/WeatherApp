<script setup>
import { ref } from 'vue'
import Weather from './components/Weather.vue'
import Search from './components/Search.vue'
import WeatherDetails from './components/WeatherDetails.vue'

// Udawany worek danych z OpenWeatherMap (zmienna reaktywna)
const weatherData = ref({
  name: "Warszawa",
  main: {
    temp: 18.5,
    feels_like: 17.2,
    pressure: 1015,
    humidity: 62
  },
  wind: {
    speed: 4.1
  },
  clouds: {
    all: 75
  },
  visibility: 10000,
  weather: [
    {
      description: "broken clouds",
      icon: "04d"
    }
  ]
})
</script>

<template>
  <main>
    <Search /> 
    
    <!-- Przekazujemy dane do karty za pomocą propsa :weatherData -->
    <Weather :weatherData="weatherData" />
    
    <!-- Przekazujemy dane do detali za pomocą propsa :weatherData -->
    <WeatherDetails :weatherData="weatherData" />
  </main>
</template>