<script setup>
import { ref } from 'vue'
import Weather from './components/Weather.vue'
import Search from './components/Search.vue'
import WeatherDetails from './components/WeatherDetails.vue'
import Recommendations from './components/Recommendations.vue'

const weatherData = ref({
  name: "Warszawa",
  main: {
    temp: 18.5,
    feels_like: 17.2,
    pressure: 1015,
    humidity: 66
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
  <main class="app-layout">
    
    <div class="search-wrapper">
      <Search :weatherData="weatherData" /> 
    </div>
    
    <div class="content-wrapper">
      
      <div class="left-side">
        <Weather :weatherData="weatherData" />
      </div>
      
      <div class="right-side">
        <WeatherDetails :weatherData="weatherData" />
        <Recommendations :weatherData="weatherData" />
      </div>

    </div>
  </main>
</template>

<style>
html, body {
  margin: 0;
  padding: 0;
  min-height: 100%;
  background: rgba(0, 0, 0, 0.1) url(@/assets/background-weather3.jpeg);
  background-blend-mode: overlay;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  font-family: Roboto, sans-serif;
}

.app-layout {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.search-wrapper {
  width: 100%;
  margin-bottom: 20px;
}

/* Domyślny układ mobilny: wszystko leci po kolei w dół */
.content-wrapper {
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
  width: 100%;
  padding: 20px;
}

.right-side {
  display: flex;
  flex-direction: column;
  gap: 20px;
  width: 100%;
  max-width: 450px;
}

/* DUŻE EKRANY: Ustawiamy lewą i prawą stronę obok siebie */
@media (min-width: 992px) {
  .content-wrapper {
    flex-direction: row;     
    justify-content: center; 
    align-items: stretch; /* Rozciąga obie strony do tej samej wysokości, dając efekt kwadratu */
    gap: 30px;
  }

  .left-side, .right-side {
    margin: 0 !important;
  }

  /* Resetujemy marginesy komponentów wewnątrz, bo flexbox pilnuje odstępów */
  .left-side > *, .right-side > * {
    margin: 0 !important;
  }
}
</style>