<script setup>
import { ref } from 'vue'
import Weather from './components/Weather.vue'
import Search from './components/Search.vue'
import WeatherDetails from './components/WeatherDetails.vue'

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
      <Weather :weatherData="weatherData" />
      <WeatherDetails :weatherData="weatherData" />
    </div>
  </main>
</template>

<style>
/* Resetujemy domyślne marginesy przeglądarki */
html, body {
  margin: 0;
  padding: 0;
  min-height: 100%;
  background-image: url(@/assets/background.jpg);
  
  font-family: sans-serif;
}

/* Główny kontener aplikacji */
.app-layout {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

/* Wyszukiwarka wycentrowana na środku */
.search-wrapper {
  width: 100%;
  margin-bottom: 20px;
}

/* Domyślny układ dla telefonów (pionowy) */
.content-wrapper {
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
  width: 100%;
}

/* Magiczny moment: dla ekranów powyżej 992px (komputery/tablety) elementy stają obok siebie */
@media (min-width: 992px) {
  .content-wrapper {
    flex-direction: row;     /* Zmień układ na poziomy (obok siebie) */
    justify-content: center; /* Wyśrodkuj oba elementy na ekranie */
    align-items: flex-start; /* Wyrównaj je równo od górnej krawędzi */
  }

  /* Usuwamy domyślne wielkie marginesy z komponentów, bo teraz Flexbox pilnuje odstępów */
  .content-wrapper > * {
    margin: 0 !important;
  }
}
</style>