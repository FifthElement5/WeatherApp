<script setup>
// Otwieramy drzwi i przyjmujemy paczkę z danymi z App.vue
defineProps({
  weatherData: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div class="details-container mx-auto my-4">
    <div class="row no-gutters text-center text-white rounded shadow-sm">
      
      <div class="col-6 detail-box p-3 border-right border-bottom">
        <span class="lnr lnr-user detail-icon"></span>
        <p class="detail-label mb-1">Odczuwalna</p>
        <h4 class="detail-value m-0">{{ weatherData.main.feels_like }}°C</h4>
      </div>

      <div class="col-6 detail-box p-3 border-bottom">
        <span class="lnr lnr-drop detail-icon"></span>
        <p class="detail-label mb-1">Wilgotność</p>
        <h4 class="detail-value m-0">{{ weatherData.main.humidity }}%</h4>
      </div>

      <div class="col-6 detail-box p-3 border-right">
        <span class="lnr lnr-chart-bars detail-icon"></span>
        <p class="detail-label mb-1">Ciśnienie</p>
        <h4 class="detail-value m-0">{{ weatherData.main.pressure }} hPa</h4>
      </div>

      <div class="col-6 detail-box p-3">
        <span class="lnr lnr-rocket detail-icon"></span>
        <p class="detail-label mb-1">Wiatr</p>
        <h4 class="detail-value m-0">{{ weatherData.wind.speed }} m/s</h4>
      </div>

    </div>
  </div>
</template>

<style scoped>
/* Powrót do Linearicons */
@import url("https://cdn.linearicons.com/free/1.0.0/icon-font.min.css");

.details-container {
  max-width: 450px;
  width: 100%;
  font-family: 'Montserrat', sans-serif;
}

.row {
  /* Efekt przezroczystości i rozmycia z pierwszej karty */
  background: linear-gradient(135deg, rgba(81, 99, 149, 0.3) 0%, rgba(97, 67, 133, 0.3) 100%);
  backdrop-filter: blur(15px);
  -webkit-backdrop-filter: blur(15px);
  overflow: hidden;
}

.detail-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 125px;
}

.detail-icon {
  font-size: 32px; /* Zwiększony rozmiar dla starych ikon */
  color: #ffffff;
  text-shadow: 1px 1px 5px rgba(0, 0, 0, 0.15);
  margin-bottom: 10px;
}

.detail-label {
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: rgba(255, 255, 255, 0.75);
}

.detail-value {
  font-size: 18px;
  font-weight: 600;
  color: #ffffff;
  text-shadow: 1px 1px 4px rgba(0, 0, 0, 0.15);
}

.border-right {
  border-right: 1px solid rgba(255, 255, 255, 0.15) !important;
}

.border-bottom {
  border-bottom: 1px solid rgba(255, 255, 255, 0.15) !important;
}

@media (min-width: 768px) {
  .details-container {
    max-width: 450px;
  }
}
</style>