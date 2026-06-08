<script setup>
// Odbieramy dane z góry, żeby móc wyświetlić aktualną nazwę miasta obok ikony
defineProps({
  weatherData: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div class="search-container mx-auto my-4">
    
    <div class="info-bar mb-4">
      <div class="info-title">Prognoza pogody</div>
      <div class="info-location">
        <span class="lnr lnr-map-marker location-icon"></span>
        {{ weatherData.name }}
      </div>
    </div>

    <div class="input-group">
      <input 
        type="text" 
        class="form-control search-input" 
        placeholder="Wpisz nazwę miasta (np. Warszawa)..."
      />
      <div class="input-group-append">
        <button class="btn btn-search" type="button">
          Szukaj
        </button>
      </div>
    </div>

  </div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,500,600,700,800,900");
@import url("https://cdn.linearicons.com/free/1.0.0/icon-font.min.css");

/* Dopasowujemy styl wyszukiwarki do Twojej karty pogodowej */
.search-container {
  max-width: 450px; /* Domyślne ograniczenie na małe ekrany */
  width: 100%;
}

.search-input {
  border-radius: 20px 0 0 20px !important;
  border: 2px solid #516395;
  padding: 25px 20px;
  font-family: 'Montserrat', sans-serif;
}

.search-input:focus {
  border-color: #614385;
  box-shadow: none;
}

.btn-search {
  background: linear-gradient(135deg, #516395 0%, #614385 100%);
  color: white;
  border: none;
  border-radius: 0 20px 20px 0 !important;
  padding: 0 25px;
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
}

.btn-search:hover {
  background: linear-gradient(135deg, #614385 0%, #516395 100%);
  color: white;
}

/* STYLOWANIE PASKA INFORMACYJNEGO */
.info-bar {
  display: flex;
  flex-direction: column; /* Na małym ekranie: jeden pod drugim */
  align-items: center;
  gap: 10px;
  width: 100%;
}

.info-title {
  font-size: 24px;
  font-weight: 700;
  color: #516395;
}

.info-location {
  font-size: 18px;
  font-weight: 500;
  color: #614385;
  display: flex;
  align-items: center;
  gap: 5px;
}

.location-icon {
  color: #516395;
  font-weight: bold;
}

/* DUŻE EKRANY (Komputery/Tablety) */
@media (min-width: 992px) {
  /* Cały kontener wyszukiwarki może się rozszerzyć na dużym ekranie */
  .search-container {
    max-width: 920px; 
  }

  /* Pasek informacyjny układa się obok siebie */
  .info-bar {
    flex-direction: row;
    justify-content: space-between; /* Rozsuwa tytuł i miasto na boki */
    margin-bottom: 25px !important;
  }
}
</style>