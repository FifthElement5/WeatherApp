<template>
  <nav class="top-navbar">
    <div class="nav-container">
      
      <div class="brand">
        <img src="@/assets/logoWeatherApp192.png" alt="Logo" class="logo-img" />
        <span class="brand-name">Pogodynka</span>
      </div>
      
      <div class="nav-actions">
        <button class="nav-btn">
          <span class="lnr lnr-cog"></span>
        </button>
      </div>

    </div>
  </nav>
</template>

<style scoped>
@import url("https://cdn.linearicons.com/free/1.0.0/icon-font.min.css");

.top-navbar {
  /* Rozciąganie na pełną szerokość ekranu */
  width: 100vw; 
  position: relative;
  left: 50%;
  right: 50%;
  margin-left: -50vw;
  margin-right: -50vw;
  
  padding: 15px 0;
  margin-bottom: 40px;
  
  /* Ciemne, mocno przezroczyste tło */
  background: rgba(10, 10, 15, 0.5) !important;
  
  /* Efekt rozmycia tła (szkło) */
  backdrop-filter: blur(12px) !important;
  -webkit-backdrop-filter: blur(12px) !important;
  
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}

.nav-container {
  /* Zawartość wewnątrz paska nadal trzyma się ładnego środka */
  max-width: 1000px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}

.brand {
  display: flex;
  align-items: center;
  gap: 12px;
}

/* Style dla Twojego obrazka logo */
.logo-img {
  height: 35px; /* Wysokość logo, dopasuj do siebie */
  width: auto;
  object-fit: contain;
}

.brand-name {
  color: #ffffff;
  font-weight: 700;
  font-size: 20px;
  letter-spacing: 1px;
  font-family: 'Montserrat', sans-serif;
}

.nav-btn {
  background: transparent;
  border: none;
  color: rgba(255, 255, 255, 0.6);
  font-size: 20px;
  cursor: pointer;
}
</style>