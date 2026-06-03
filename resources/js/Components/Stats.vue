<template>
  <section class="stats" ref="statsSection">
    
    <div class="card">
      <h2>{{ animatedStats.followers }}K+</h2>
      <p>Abonnés générés</p>
    </div>

    <div class="card">
      <h2>+{{ animatedStats.growth }}%</h2>
      <p>Croissance</p>
    </div>

    <div class="card">
      <h2>{{ animatedStats.projects }}+</h2>
      <p>Projets réalisés</p>
    </div>

    <div class="card">
      <h2>{{ animatedStats.clients }}</h2>
      <p>Client actif</p>
    </div>

  </section>
</template>

<script setup>
import { ref, reactive, onMounted } from 'vue';

// Référence pour observer la section au défilement
const statsSection = ref(null);

// Valeurs de départ réactives initialisées à 0
const animatedStats = reactive({
  followers: 0,
  growth: 0,
  projects: 0,
  clients: 0
});

// Objectifs finaux à atteindre
const targetStats = {
  followers: 36,
  growth: 2471,
  projects: 4,
  clients: 1
};

// Fonction d'animation fluide
const animateStats = () => {
  const duration = 2000; // Durée de l'effet de compteur (2 secondes)
  const frameRate = 1000 / 60; // Rafraîchissement à 60 images par seconde
  const totalFrames = Math.round(duration / frameRate);
  let frame = 0;

  const interval = setInterval(() => {
    frame++;
    const progress = frame / totalFrames;

    if (frame <= totalFrames) {
      animatedStats.followers = Math.round(targetStats.followers * progress);
      animatedStats.growth = Math.round(targetStats.growth * progress);
      animatedStats.projects = Math.round(targetStats.projects * progress);
      animatedStats.clients = Math.round(targetStats.clients * progress);
    } else {
      // Sécurité pour forcer l'affichage exact à la fin de l'animation
      animatedStats.followers = targetStats.followers;
      animatedStats.growth = targetStats.growth;
      animatedStats.projects = targetStats.projects;
      animatedStats.clients = targetStats.clients;
      clearInterval(interval);
    }
  }, frameRate);
};

// Détection de l'apparition de la section à l'écran
onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        animateStats();
        observer.unobserve(entry.target); // L'effet ne s'exécute qu'une seule fois au scroll
      }
    });
  }, { threshold: 0.2 }); // Déclenchement dès que 20% de la section est visible

  if (statsSection.value) {
    observer.observe(statsSection.value);
  }
});
</script>

<style scoped>
/* Grille principale adaptée au fond neutre clair */
.stats {
  display: grid;
  /* 4 colonnes par défaut sur grand écran (Ordinateur) */
  grid-template-columns: repeat(4, 1fr);
  gap: 25px;
  padding: 60px 20px;
  max-width: 1200px;
  margin: 0 auto;
}

/* Design épuré, pro et neutre pour vos cartes statistiques */
.card {
  padding: 40px 20px; /* Réduction légère du padding horizontal pour éviter les débordements */
  text-align: center;
  border-radius: 20px;
  background: #ffffff;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.04);
  border: 1px solid #f1f5f9;
  transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
}

/* Chiffres en grand, gras et en Times New Roman */
.card h2 {
  font-family: 'Times New Roman', Times, serif;
  color: #2563eb; 
  font-size: 3.5rem;
  font-weight: bold;
  margin: 0 0 10px 0;
  white-space: nowrap; /* Empêche le chiffre et le symbole (+ / K) de se couper en deux */
}

/* Textes sous les stats en Arial simple et un peu bold */
.card p {
  font-family: Arial, sans-serif;
  font-weight: bold; 
  font-size: 16px;
  color: #475569; 
  margin: 0;
}

/* Interaction subtile au survol de la souris */
.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(37, 99, 235, 0.08);
  border-color: #bfdbfe;
}

/* --- RESPONSIVE DESKTOP PETIT & TABLETTE --- */
@media (max-width: 1024px) {
  .stats {
    /* Équilibre parfait : un carré de 2x2 sur les tablettes */
    grid-template-columns: repeat(2, 1fr);
  }
}

/* --- RESPONSIVE SMARTPHONES --- */
@media (max-width: 600px) {
  .stats {
    /* 1 seule colonne sur mobile pour donner de l'espace aux grands chiffres */
    grid-template-columns: 1fr;
    gap: 15px; /* On réduit un peu l'espace entre les cartes sur mobile */
  }

  .card h2 {
    font-size: 2.8rem; /* Chiffres légèrement plus petits pour éviter les bugs d'affichage */
  }
  
  .card {
    padding: 30px 15px; /* Un peu moins de vide interne sur petit écran */
  }
}

/* Design épuré, pro et neutre pour vos cartes statistiques */
.card {
  padding: 40px;
  text-align: center;
  border-radius: 20px;
  background: #ffffff;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.04);
  border: 1px solid #f1f5f9;
  transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
}

/* Chiffres en grand, gras et en Times New Roman */
.card h2 {
  font-family: 'Times New Roman', Times, serif;
  color: #2563eb; /* Bleu vif pro pour faire ressortir l'impact de la donnée */
  font-size: 3.5rem;
  font-weight: bold;
  margin: 0 0 10px 0;
}

/* Textes sous les stats en Arial simple et un peu bold */
.card p {
  font-family: Arial, sans-serif;
  font-weight: bold; /* Donne du caractère et de la lisibilité sur fond clair */
  font-size: 16px;
  color: #475569; /* Gris ardoise élégant */
  margin: 0;
}

/* Interaction subtile au survol de la souris */
.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(37, 99, 235, 0.08);
  border-color: #bfdbfe;
}

/* Ajustements responsives pour téléphones */
@media (max-width: 600px) {
  .card h2 {
    font-size: 2.8rem;
  }
}
</style>