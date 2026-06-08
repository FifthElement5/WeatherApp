<template>
  <div class="search-container mx-auto my-4">
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
/* Dopasowujemy styl wyszukiwarki do Twojej karty pogodowej */
.search-container {
  max-width: 450px; /* Taka sama szerokość jak karta pogody */
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
</style>