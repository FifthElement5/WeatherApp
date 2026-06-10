<script setup>
import { ref, onMounted } from 'vue'
import Weather from './components/Weather.vue'
import Search from './components/Search.vue'
import WeatherDetails from './components/WeatherDetails.vue'
import Recommendations from './components/Recommendations.vue'
import Navbar from './components/Navbar.vue'

// Twój nowy klucz API
const API_KEY = '36801d9059d4683e891dadc95ffb1710'

// TWÓJ ORYGINALNY MOCK - nic w nim nie zmieniamy, nazwa zostaje ta sama!
const weatherData = ref({
  name: "Warszawa (Test)",
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
  ],
  sys: {
    country: "PL",
    sunrise: 1717900000,
    sunset: 1717950000
  }
})

// Prosta funkcja, która tylko bierze dane z internetu i wkłada je do Twojego mocka
const fetchWeather = async (city) => {
  try {
    const response = await fetch(
      `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${API_KEY}&units=metric&lang=pl`
    )
    
    if (!response.ok) {
      alert('Nie znaleziono miasta!')
      return
    }
    
    const data = await response.json()
    // Nadpisujemy Twój mock danymi z internetu - struktura z API pasuje do Twojego mocka!
    weatherData.value = data 
  } catch (error) {
    console.error("Błąd pobierania:", error)
  }
}

// Po uruchomieniu pobieramy prawdziwą pogodę dla Warszawy
onMounted(() => {
  fetchWeather('Zielona Góra') 
})
</script>

<template>
<Navbar />
  <main class="app-layout">
   
    <div class="search-wrapper">
     
      <Search :weatherData="weatherData" @search-city="fetchWeather" />
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
  background: url(@/assets/background-weather4.jpg);
  background-attachment: fixed;
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