<template>
  <section id="process" ref="processSection">
    <div class="container">

      <!-- En-tête de la section -->
      <div class="title">
        <h2>Mon Processus</h2>
        <p class="subtitle">Une méthode claire pour garantir les résultats.</p>
      </div>

      <!-- Chronologie / Timeline en Grille -->
      <div class="timeline">

        <!-- ÉTAPE 1 -->
        <div class="step">
          <span class="number">{{ formatNumber(animatedSteps.step1) }}</span>
          <h3>Audit & Analyse</h3>
        </div>

        <!-- ÉTAPE 2 -->
        <div class="step">
          <span class="number">{{ formatNumber(animatedSteps.step2) }}</span>
          <h3>Stratégie Éditoriale</h3>
        </div>

        <!-- ÉTAPE 3 -->
        <div class="step">
          <span class="number">{{ formatNumber(animatedSteps.step3) }}</span>
          <h3>Création de Contenu</h3>
        </div>

        <!-- ÉTAPE 4 -->
        <div class="step">
          <span class="number">{{ formatNumber(animatedSteps.step4) }}</span>
          <h3>Publication & Suivi</h3>
        </div>

        <!-- ÉTAPE 5 -->
        <div class="step">
          <span class="number">{{ formatNumber(animatedSteps.step5) }}</span>
          <h3>Reporting</h3>
        </div>

      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, reactive, onMounted } from 'vue';

// Référence pour observer la section au défilement
const processSection = ref(null);

// Les valeurs initiales qui débutent toutes à 0
const animatedSteps = reactive({
  step1: 0,
  step2: 0,
  step3: 0,
  step4: 0,
  step5: 0
});

// Les cibles finales pour chaque étape
const targetSteps = {
  step1: 1,
  step2: 2,
  step3: 3,
  step4: 4,
  step5: 5
};

// Fonction utilitaire pour ajouter un zéro devant les chiffres uniques (ex: 01, 02)
const formatNumber = (num) => {
  return num < 10 ? `0${num}` : num;
};

// Fonction gérant l'animation du compteur progressif
const animateTimeline = () => {
  const duration = 1200; // Durée globale de l'animation en millisecondes
  const frameRate = 1000 / 60; // 60 frames par seconde
  const totalFrames = Math.round(duration / frameRate);
  let frame = 0;

  const interval = setInterval(() => {
    frame++;
    const progress = frame / totalFrames;

    if (frame <= totalFrames) {
      animatedSteps.step1 = Math.round(targetSteps.step1 * progress);
      animatedSteps.step2 = Math.round(targetSteps.step2 * progress);
      animatedSteps.step3 = Math.round(targetSteps.step3 * progress);
      animatedSteps.step4 = Math.round(targetSteps.step4 * progress);
      animatedSteps.step5 = Math.round(targetSteps.step5 * progress);
    } else {
      // Sécurité pour caler les chiffres finaux précis
      animatedSteps.step1 = targetSteps.step1;
      animatedSteps.step2 = targetSteps.step2;
      animatedSteps.step3 = targetSteps.step3;
      animatedSteps.step4 = targetSteps.step4;
      animatedSteps.step5 = targetSteps.step5;
      clearInterval(interval);
    }
  }, frameRate);
};

// Déclenchement de l'animation à l'apparition de la section à l'écran
onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        animateTimeline();
        observer.unobserve(entry.target); // L'effet ne se joue qu'une seule fois
      }
    });
  }, { threshold: 0.15 }); // Se lance lorsque 15% de la section est visible

  if (processSection.value) {
    observer.observe(processSection.value);
  }
});
</script>

<style scoped>
/* Structure globale - Fond neutre clair pro */
#process {
  padding: 80px 20px;
  background-color: #f8fafc; /* Même fond neutre épuré */
  color: #1e293b;
}

.container {
  max-width: 1200px;
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
  color: #0f172a;
  margin-bottom: 10px;
}

.title .subtitle {
  font-family: Arial, sans-serif;
  font-weight: bold;
  font-size: 18px;
  color: #64748b;
}

/* Grille de la chronologie */
.timeline {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 25px;
}

/* Cartes étapes adaptées au style neutre et chic */
.step {
  text-align: center;
  background: #ffffff;
  padding: 40px 25px;
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.04);
  border: 1px solid #f1f5f9;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

/* Le rond numérique animé */
.number {
  display: inline-flex;
  width: 65px;
  height: 65px;
  border-radius: 50%;
  align-items: center;
  justify-content: center;
  
  /* Nouveau dégradé bleu professionnel et éclatant */
  background: linear-gradient(135deg, #2563eb, #1d4ed8);
  color: #ffffff;
  
  font-family: Arial, sans-serif;
  font-weight: bold;
  font-size: 20px;
  margin-bottom: 25px;
  box-shadow: 0 4px 15px rgba(37, 99, 235, 0.3);
}

/* Titres d'étapes */
.step h3 {
  font-family: 'Times New Roman', Times, serif;
  font-size: 20px;
  font-weight: bold;
  color: #0f172a;
  margin: 0;
  line-height: 1.4;
}

/* Interaction moderne au survol */
.step:hover {
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(37, 99, 235, 0.08);
  border-color: #bfdbfe;
}

/* Ajustements pour les versions smartphones */
@media (max-width: 768px) {
  .title h2 {
    font-size: 34px;
  }
  .step {
    padding: 30px 20px;
  }
}
</style>