<template>
  <div class="details-container mx-auto my-4">
    <div class="row no-gutters text-center text-white rounded shadow-sm">
      
      <div class="col-6 col-md-3 detail-box p-3 border-right border-bottom border-md-bottom-0">
        <span class="lnr lnr-user detail-icon"></span>
        <p class="detail-label mb-1">Odczuwalna</p>
        <h4 class="detail-value m-0">18°C</h4>
      </div>

      <div class="col-6 col-md-3 detail-box p-3 border-md-right border-bottom border-md-bottom-0">
        <span class="lnr lnr-drop detail-icon"></span>
        <p class="detail-label mb-1">Wilgotność</p>
        <h4 class="detail-value m-0">65%</h4>
      </div>

      <div class="col-6 col-md-3 detail-box p-3 border-right">
        <span class="lnr lnr-chart-bars detail-icon"></span>
        <p class="detail-label mb-1">Ciśnienie</p>
        <h4 class="detail-value m-0">1015 hPa</h4>
      </div>

      <div class="col-6 col-md-3 detail-box p-3">
        <span class="lnr lnr-rocket detail-icon"></span>
        <p class="detail-label mb-1">Wiatr</p>
        <h4 class="detail-value m-0">5 m/s</h4>
      </div>

    </div>
  </div>
</template>

<style scoped>
/* Import ikon Linearicons, żeby ikony detali działały tak samo jak w karcie głównej */
@import url("https://cdn.linearicons.com/free/1.0.0/icon-font.min.css");

.details-container {
  max-width: 450px; /* Taka sama szerokość jak karta i wyszukiwarka */
  font-family: 'Montserrat', sans-serif;
}

/* Tło dla kafelków z tym samym gradientem co reszta aplikacji */
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

/* Styl dla ikon */
.detail-icon {
  font-size: 24px;
  color: #a1c4fd;
  margin-bottom: 8px;
}

/* Styl dla małych podpisów */
.detail-label {
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: rgba(255, 255, 255, 0.7);
}

/* Styl dla głównych liczb */
.detail-value {
  font-size: 18px;
  font-weight: 600;
}

/* Linie podziału dostosowane do Bootstrapa 4 */
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