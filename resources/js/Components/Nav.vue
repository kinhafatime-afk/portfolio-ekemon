<template>
  <header class="header">

    <div class="logo">
      <span>EKEMON</span>
    </div>

    <nav :class="['nav', { active: isOpen }]" @click="isOpen = false">
      <a href="#hero">Accueil</a>
      <a href="#about">À propos</a>
      <a href="#services">Services</a>
      <a href="#projects">Réalisations</a>
      <a href="#contact">Contact</a>
    </nav>

    <button class="menu-btn" @click="isOpen = !isOpen" aria-label="Menu de navigation">
      <Menu v-if="!isOpen" />
      <X v-else />
    </button>

  </header>
</template>

<script setup>
import { ref } from 'vue'
import { Menu, X } from 'lucide-vue-next'

const isOpen = ref(false)
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 80px; /* On fixe la hauteur du header pour caler proprement le menu mobile */

  display: flex;
  justify-content: space-between;
  align-items: center;

  padding: 0 8%; /* Ajustement du padding (0 haut/bas car géré par height) */

  backdrop-filter: blur(15px);
  background: rgba(15, 23, 42, .75); /* Légèrement plus opaque pour garantir la lisibilité */
  border-bottom: 1px solid rgba(255, 255, 255, .1);
  z-index: 1000;
}

.logo {
  font-size: 28px;
  font-weight: 700;
  color: #fff;
}

.nav {
  display: flex;
  gap: 35px;
}

.nav a {
  color: white;
  text-decoration: none;
  font-family: Arial, sans-serif;
  font-weight: 550;
  transition: .3s;
}

.nav a:hover {
  color: #60a5fa;
}

.menu-btn {
  display: none;
  background: none;
  border: none;
  color: white;
  cursor: pointer;
}

/* --- RESPONSIVE MOBILE & TABLETTE --- */
@media (max-width: 768px) {
  .nav {
    position: fixed;
    top: 80px; /* S'aligne parfaitement sous le header */
    right: -100%;
    
    width: 280px;
    /* Calcul parfait pour éviter que le menu dépasse en bas de l'écran du smartphone */
    height: calc(100vh - 80px); 
    
    background: #0f172a;
    box-shadow: -10px 10px 30px rgba(0, 0, 0, 0.2); /* Ombre légère pour détacher le menu du fond */

    flex-direction: column;
    justify-content: flex-start;
    gap: 30px;
    padding: 40px;
    transition: .4s ease-in-out;
  }

  .nav.active {
    right: 0;
  }

  .menu-btn {
    display: block;
    /* Grossit un peu l'icône sur mobile pour que ce soit facile à cliquer avec le pouce */
    transform: scale(1.2); 
  }
}
</style>