<script setup>
import { computed } from 'vue'

const props = defineProps({
  weatherData: {
    type: Object,
    required: true
  }
})

// Logika dobierająca teraz wyłącznie zestawy ikon dla danej temperatury
const recommendation = computed(() => {
  const temp = props.weatherData.main.temp

  if (temp >= 25) {
    return {
      bg: 'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?q=80&w=500',
      icons: ['lnr-sun', 'lnr-heart', 'lnr-smile'] // słońce, serce, uśmiech
    }
  } else if (temp >= 15 && temp < 25) {
    return {
      bg: 'https://images.unsplash.com/photo-1473448912268-2022ce9509d8?q=80&w=500',
      icons: ['lnr-smile', 'lnr-bicycle', 'lnr-leaf'] // uśmiech, rower, liść
    }
  } else if (temp >= 5 && temp < 15) {
    return {
      bg: 'https://images.unsplash.com/photo-1506744038136-46273834b3fb?q=80&w=500',
      icons: ['lnr-shirt', 'lnr-coffee-cup', 'lnr-neutral'] // koszulka/bluza, kubek, neutralny
    }
  } else {
    return {
      bg: 'https://images.unsplash.com/photo-1485594050903-8e8ee7b071a8?q=80&w=500',
      icons: ['lnr-snowflake', 'lnr-home', 'lnr-sad'] // płatek śniegu, dom, smutny
    }
  }
})
</script>

<template>
  <div class="rec-container mx-auto my-4 rounded shadow-sm">
    <!-- Zdjęcie zajmuje górną, największą część kafelka -->
    <div class="rec-image" :style="{ backgroundImage: `url(${recommendation.bg})` }"></div>
    
    <!-- Sekcja na dole: same duże, wyśrodkowane ikony -->
    <div class="rec-icons-box p-3">
      <span 
        v-for="(icon, index) in recommendation.icons" 
        :key="index" 
        :class="['lnr', icon, 'rec-icon']"
      ></span>
    </div>
  </div>
</template>

<style scoped>
@import url("https://cdn.linearicons.com/free/1.0.0/icon-font.min.css");

.rec-container {
  max-width: 450px;
  width: 100%;
  font-family: 'Montserrat', sans-serif;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  height: 315px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  padding: 20px;
  
  /* Lekko przezroczyste białe tło (75% krycia) */
  background: rgba(255, 255, 255, 0.75) !important;
  backdrop-filter: none !important;
  -webkit-backdrop-filter: none !important;
}

.rec-image {
  width: 100%;
  height: 220px; /* Zwiększyłem wysokość zdjęcia, bo nie ma już tekstów */
  background-size: cover;
  background-position: center;
  flex-shrink: 0;
}

.rec-icons-box {
  flex-grow: 1;
  display: flex;
  align-items: center;
  justify-content: center; /* Centrujemy ikony w rzędzie */
  gap: 30px; /* Odstępy między ikonami */
  background: transparent;
}

.rec-icon {
  font-size: 32px; /* Ikony są teraz duże i czytelne */
  color: #222222; /* Ciemny, elegancki kolor ładnie kontrastujący z białawym tłem */
  transition: transform 0.2s ease;
}

.rec-icon:hover {
  transform: scale(1.15); /* Delikatny efekt po najechaniu myszką */
}
</style>