<template>
  <section id="projects">
    <div class="container">

      <div class="title">
        <h2>Mes Réalisations</h2>
        <p class="subtitle">Quelques projets sur lesquels j'ai travaillé</p>
      </div>

      <div class="projects-grid">

        <div class="card">
          <div class="image-container">
             <img :src="'/images/iboukoun_cosmetics.jpeg'" alt="Suivi de page IBOUKOUN COSMETICS">
            <div class="badge">Client Actif</div>
          </div>
          <div class="card-content">
            <h3>IBOUKOUN COSMETICS</h3>
            <p>
              Gestion des réseaux sociaux, création de contenu,
              engagement communautaire et fidélisation.
            </p>
            <div class="project-stats">
              <span class="stat-growth">1 400 → 36 000 abonnés</span>
              <span class="stat-percent">+2471%</span>
            </div>
          </div>
        </div>

        <div class="card">
          <div class="image-container">
            <img :src="'/images/korico.jpeg'" alt="Suivi de page KOBOUROU CINE ROOM" />
            <div class="badge">Bénévole</div>
          </div>
          <div class="card-content">
            <h3>KOBOUROU CINE ROOM</h3>
            <p>
              Promotion de la salle de cinéma,
              animation de communauté et visibilité digitale.
            </p>
          </div>
        </div>

        <div class="card">
          <div class="image-container">
            <img :src="'/images/saint_tony.jpeg'" alt="Suivi de page BOUTIQUE SAINT TONY" />
            <div class="badge">Bénévole</div>
          </div>
          <div class="card-content">
            <h3>BOUTIQUE SAINT TONY</h3>
            <p>
              Création de contenus et mise en avant
              des produits sur les réseaux sociaux.
            </p>
          </div>
        </div>

        <div class="card">
          <div class="image-container">
           <img :src="'/images/protege_ton_enfant.jpeg'" alt="Suivi de page PROTÈGE TON ENFANT">
            <div class="badge">Projet Social</div>
          </div>
          <div class="card-content">
            <h3>PROTÈGE TON ENFANT</h3>
            <p>
              Sensibilisation sur la protection de l'enfance
              et animation de communauté.
            </p>
          </div>
        </div>

      </div>

    </div>
  </section>
</template>

<style scoped>
/* Structure de base - Fond neutre clair pro */
#projects {
  padding: 80px 20px;
  background-color: #f8fafc; /* Gris neutre très doux et élégant */
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
/* Grille principale */
.projects-grid {
  display: grid;
  /* Force l'affichage sur 2 colonnes égales sur grand écran */
  grid-template-columns: repeat(2, 1fr); 
  gap: 30px;
}

/* Version responsive pour tablette et mobile */
@media (max-width: 768px) {
  .title h2 {
    font-size: 34px;
  }
  
  /* Repasse sur 1 seule colonne sur les petits écrans pour éviter que ce soit trop serré */
  .projects-grid {
    grid-template-columns: 1fr;
  }
}

/* Design de la carte projet (Épuré, blanc et moderne) */
.card {
  background: #ffffff;
  border-radius: 20px;
  overflow: hidden; /* Permet de contenir l'image arrondie proprement */
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.04);
  border: 1px solid #f1f5f9;
  transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
  display: flex;
  flex-direction: column;
}

/* Zone Image et Badge superposé */
.image-container {
  position: relative;
  width: 100%;
  height: 200px;
  background-color: #f1f5f9; /* Fallback si l'image charge lentement */
}

.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover; /* Ajuste l'image de suivi sans la déformer */
  display: block;
}

/* Le badge repositionné de façon moderne par-dessus l'image */
.badge {
  position: absolute;
  top: 15px;
  left: 15px;
  background: linear-gradient(135deg, #2563eb, #1d4ed8); /* Dégradé de bleu pro */
  color: #ffffff;
  padding: 6px 14px;
  border-radius: 50px;
  font-family: Arial, sans-serif;
  font-weight: bold;
  font-size: 0.75rem;
  letter-spacing: 0.5px;
  box-shadow: 0 4px 10px rgba(37, 99, 235, 0.25);
}

/* Contenu textuel de la carte */
.card-content {
  padding: 25px;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

/* Titres des projets */
.card h3 {
  font-family: 'Times New Roman', Times, serif;
  font-size: 22px;
  font-weight: bold;
  color: #0f172a;
  margin: 0 0 12px 0;
}

/* Paragraphes en Arial Simple un peu Bold */
.card p {
  font-family: Arial, sans-serif;
  font-weight: 550; /* Légèrement bold pour une visibilité au top */
  font-size: 15px;
  color: #475569;
  line-height: 1.6;
  margin: 0 0 20px 0;
  flex-grow: 1; /* Aligne le bas des cartes si les textes ont des longueurs différentes */
}

/* Zone Statistiques pour Iboukoun Cosmetics */
.project-stats {
  padding-top: 15px;
  border-top: 1px solid #f1f5f9;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-family: Arial, sans-serif;
  font-weight: bold;
  font-size: 14px;
}

.stat-growth {
  color: #64748b;
}

.stat-percent {
  color: #2563eb; /* Le pourcentage de croissance ressort en bleu vif */
  font-size: 16px;
}

/* Effet interactif moderne au survol */
.card:hover {
  transform: translateY(-6px);
  box-shadow: 0 20px 40px rgba(37, 99, 235, 0.08);
  border-color: #bfdbfe;
}

/* Version responsive pour mobile */
@media (max-width: 768px) {
  .title h2 {
    font-size: 34px;
  }
}
</style>