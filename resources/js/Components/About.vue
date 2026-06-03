<template>
  <section id="about" ref="aboutSection">
    <div class="container">
      
      <!-- En-tête de la section -->
      <div class="title">
        <h2>À propos de moi</h2>
        <p class="subtitle">Community Manager & Créateur de contenu</p>
      </div>

      <!-- Grille à deux colonnes -->
      <div class="about-grid">
        
        <!-- COLONNE GAUCHE : Informations et Compétences -->
        <div class="content-side">
          <h3>Ekemon Carlos MONDOTE</h3>
          <p class="description">
            Passionné par la communication digitale et la création de contenu.
            J'aide les entreprises à développer leur visibilité et à convertir leur audience en clients.
          </p>

          <!-- Liste des compétences animées -->
          <div class="skills">
            
            <div class="skill">
              <div class="skill-info">
                <span>Création de contenu</span>
                <span class="percentage">{{ animatedWidths.contenu }}%</span>
              </div>
              <div class="bar">
                <div class="fill" :style="{ width: animatedWidths.contenu + '%' }"></div>
              </div>
            </div>

            <div class="skill">
              <div class="skill-info">
                <span>Gestion de communauté</span>
                <span class="percentage">{{ animatedWidths.communaute }}%</span>
              </div>
              <div class="bar">
                <div class="fill" :style="{ width: animatedWidths.communaute + '%' }"></div>
              </div>
            </div>

            <div class="skill">
              <div class="skill-info">
                <span>Stratégie digitale</span>
                <span class="percentage">{{ animatedWidths.strategie }}%</span>
              </div>
              <div class="bar">
                <div class="fill" :style="{ width: animatedWidths.strategie + '%' }"></div>
              </div>
            </div>

          </div>
        </div>

        <!-- COLONNE DROITE : Image de la personne -->
        <div class="image-side">
          <div class="image-wrapper">
         <img :src="'/images/moi.jpeg'" alt="Ekemon Carlos MONDOTE">
          </div>
        </div>

      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, reactive, onMounted } from 'vue';

// Référence pour détecter la section à l'écran
const aboutSection = ref(null);

// Valeurs de départ (0%) pour l'effet de compteur
const animatedWidths = reactive({
  contenu: 0,
  communaute: 0,
  strategie: 0
});

// Les objectifs finaux pour chaque compétence
const targetWidths = {
  contenu: 92,
  communaute: 90,
  strategie: 85
};

// Fonction d'animation de style "compte à rebours" ascendant
const animateSkills = () => {
  const duration = 2000; // Durée totale de l'animation en millisecondes
  const frameRate = 1000 / 60; // 60 images par seconde
  const totalFrames = Math.round(duration / frameRate);
  let frame = 0;

  const interval = setInterval(() => {
    frame++;
    
    // Progression fluide basée sur un ratio
    const progress = frame / totalFrames;

    if (frame <= totalFrames) {
      animatedWidths.contenu = Math.round(targetWidths.contenu * progress);
      animatedWidths.communaute = Math.round(targetWidths.communaute * progress);
      animatedWidths.strategie = Math.round(targetWidths.strategie * progress);
    } else {
      // Sécurité pour forcer les valeurs exactes à la fin
      animatedWidths.contenu = targetWidths.contenu;
      animatedWidths.communaute = targetWidths.communaute;
      animatedWidths.strategie = targetWidths.strategie;
      clearInterval(interval);
    }
  }, frameRate);
};

// Déclenchement de l'animation au moment du scroll sur la section
onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        animateSkills();
        observer.unobserve(entry.target); // L'animation ne se joue qu'une seule fois
      }
    });
  }, { threshold: 0.2 }); // Se déclenche quand 20% de la section est visible

  if (aboutSection.value) {
    observer.observe(aboutSection.value);
  }
});
</script>

<style scoped>
/* Style général de la section (Fond neutre, clair et pro) */
#about {
  padding: 80px 20px;
  background-color: #0f172a; /* Gris neutre très doux */
  color: #1e293b; /* Texte ardoise foncé pour un excellent contraste */
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}

/* En-tête */
.title {
  text-align: center;
  margin-bottom: 60px;
}

.title h2 {
  font-family: 'Times New Roman', Times, serif;
  font-size: 42px;
  font-weight: bold;
  color: #ffffff;
  margin-bottom: 10px;
}

.title .subtitle {
  font-family: Arial, sans-serif;
  font-weight: bold;
  font-size: 18px;
  color: #ffffff;
}

/* Grille principale : Gauche (info) et Droite (image) */
.about-grid {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 50px;
  align-items: center;
}

/* Colonne Gauche : Contenu */
.content-side h3 {
  font-family: 'Times New Roman', Times, serif;
  font-size: 32px;
  color: #d3c8c8;
  margin-bottom: 20px;
}

.content-side .description {
  font-family: Arial, sans-serif;
  font-weight: 500; /* Légèrement bold pour bien faire ressortir les écrits */
  font-size: 17px;
  line-height: 1.6;
  color: #f5f5f5;
  margin-bottom: 40px;
}

/* Section Compétences */
.skill {
  margin-bottom: 25px;
}

.skill-info {
  display: flex;
  justify-content: space-between;
  font-family: Arial, sans-serif;
  font-weight: bold; /* Affichage gras pour être très lisible */
  font-size: 16px;
  color: #ececec;
  margin-bottom: 8px;
}

.percentage {
  color: #2563eb; /* Le pourcentage ressort en bleu vif */
}

/* Barres de progression */
.bar {
  height: 12px;
  background: #e2e8f0; /* Fond neutre de la barre */
  border-radius: 50px;
  overflow: hidden;
}

.fill {
  height: 100%;
  background: linear-gradient(90deg, #2563eb, #1d4ed8); /* Dégradé de bleu pro */
  border-radius: 50px;
  transition: width 0.1s linear; /* fluidité du compteur */
}

/* Colonne Droite : Image */
.image-side {
  display: flex;
  justify-content: center;
}

.image-wrapper {
  width: 100%;
  max-width: 380px;
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
  border-radius: 20px;
  overflow: hidden;
  background: #ffffff;
  padding: 10px; /* Effet cadre blanc élégant */
}

.image-wrapper img {
  width: 100%;
  height: auto;
  display: block;
  border-radius: 12px;
  object-fit: cover;
}

/* Responsive pour les écrans de smartphones et tablettes */
@media (max-width: 900px) {
  .about-grid {
    grid-template-columns: 1fr; /* Passe sur une seule colonne */
    gap: 40px;
  }
  
  /* Remet l'image au-dessus ou en dessous selon la préférence sur mobile */
  .image-side {
    order: -1; /* L'image passe au-dessus sur mobile pour un meilleur flow */
  }

  .title h2 {
    font-size: 34px;
  }
}
</style>