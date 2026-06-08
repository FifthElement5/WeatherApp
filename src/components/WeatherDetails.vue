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
      
      <div class="col-6 col-md-3 detail-box p-3 border-right border-bottom border-md-bottom-0">
        <span class="lnr lnr-user detail-icon"></span>
        <p class="detail-label mb-1">Odczuwalna</p>
        <h4 class="detail-value m-0">{{ weatherData.main.feels_like }}°C</h4>
      </div>

      <div class="col-6 col-md-3 detail-box p-3 border-md-right border-bottom border-md-bottom-0">
        <span class="lnr lnr-drop detail-icon"></span>
        <p class="detail-label mb-1">Wilgotność</p>
        <h4 class="detail-value m-0">{{ weatherData.main.humidity }}%</h4>
      </div>

      <div class="col-6 col-md-3 detail-box p-3 border-right">
        <span class="lnr lnr-chart-bars detail-icon"></span>
        <p class="detail-label mb-1">Ciśnienie</p>
        <h4 class="detail-value m-0">{{ weatherData.main.pressure }} hPa</h4>
      </div>

      <div class="col-6 col-md-3 detail-box p-3">
        <span class="lnr lnr-rocket detail-icon"></span>
        <p class="detail-label mb-1">Wiatr</p>
        <h4 class="detail-value m-0">{{ weatherData.wind.speed }} m/s</h4>
      </div>

    </div>
  </div>
</template>

<style scoped>
/* Twoje style zostają bez zmian... */
@import url("https://cdn.linearicons.com/free/1.0.0/icon-font.min.css");

.details-container {
  max-width: 450px;
  font-family: 'Montserrat', sans-serif;
}

.row {
  background: linear-gradient(135deg, #516395 0%, #614385 100%);
  overflow: hidden;
}

.detail-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.detail-icon {
  font-size: 24px;
  color: #a1c4fd;
  margin-bottom: 8px;
}

.detail-label {
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: rgba(255, 255, 255, 0.7);
}

.detail-value {
  font-size: 18px;
  font-weight: 600;
}

.border-right {
  border-right: 1px solid rgba(255, 255, 255, 0.15) !important;
}
.border-bottom {
  border-bottom: 1px solid rgba(255, 255, 255, 0.15) !important;
}

@media (min-width: 768px) {
  .border-md-bottom-0 {
    border-bottom: 0 !important;
  }
  .border-md-right {
    border-right: 1px solid rgba(255, 255, 255, 0.15) !important;
  }
}
</style>