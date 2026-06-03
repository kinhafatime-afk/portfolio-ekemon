<template>
  <section id="services">
    <div class="container">

      <!-- En-tête de la section -->
      <div class="title">
        <h2>Mes Services</h2>
        <p class="subtitle">Des solutions digitales pour développer votre présence en ligne.</p>
      </div>

      <!-- Grille de services -->
      <div class="services-grid">

        <!-- SERVICE 1 : Gestion Réseaux Sociaux -->
        <div class="service-card">
          <div class="icon-wrapper">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <rect width="14" height="20" x="5" y="2" rx="2" ry="2"/>
              <path d="M12 18h.01"/>
            </svg>
          </div>
          <h3>Gestion Réseaux Sociaux</h3>
          <p>
            Gestion professionnelle de vos pages Facebook,
            Instagram et autres réseaux sociaux.
          </p>
        </div>

        <!-- SERVICE 2 : Création de Contenu -->
        <div class="service-card">
          <div class="icon-wrapper">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="m12 3-1.912 5.886a1 1 0 0 1-.951.691H2.93a1 1 0 0 0-.588 1.81l4.947 3.593a1 1 0 0 1 .363 1.118l-1.913 5.886a1 1 0 0 0 1.54 1.118L12 19.515l4.722 3.429a1 1 0 0 0 1.54-1.118l-1.912-5.886a1 1 0 0 1 .363-1.118l4.947-3.593a1 1 0 0 0-.587-1.81H14.863a1 1 0 0 1-.951-.691z"/>
            </svg>
          </div>
          <h3>Création de Contenu</h3>
          <p>
            Création de visuels attractifs,
            publications engageantes et contenus optimisés.
          </p>
        </div>

        <!-- SERVICE 3 : Stratégie Digitale -->
        <div class="service-card">
          <div class="icon-wrapper">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M3 3v18h18"/>
              <path d="m19 9-5 5-4-4-3 3"/>
            </svg>
          </div>
          <h3>Stratégie Digitale</h3>
          <p>
            Mise en place d'une stratégie efficace
            pour développer votre visibilité.
          </p>
        </div>

        <!-- SERVICE 4 : Publicité Meta Ads -->
        <div class="service-card">
          <div class="icon-wrapper">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M4.5 16.5c-1.5 1.26-2.5 3.19-2.5 5.5s1 4.24 2.5 5.5"/>
              <path d="M12 2s8 3 8 10c0 3-1 6-3 8L12 22l-5-2c-2-2-3-5-3-8 0-7 8-10 8-10z"/>
              <path d="m9 12 2 2 4-4"/>
            </svg>
          </div>
          <h3>Publicité Meta Ads</h3>
          <p>
            Création et gestion de campagnes
            Facebook et Instagram Ads.
          </p>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
/* Structure de base - Fond neutre clair */
#services {
  padding: 80px 20px;
  background-color: #f8fafc; /* Gris neutre très doux identique à la section À Propos */
  color: #1e293b;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

/* En-tête de la section */
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

/* Grille réactive pour les cartes */
.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 30px;
}

/* Structure de base - Fond neutre clair */
#services {
  padding: 80px 20px;
  background-color: #f8fafc; /* Gris neutre très doux identique à la section À Propos */
  color: #1e293b;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

/* En-tête de la section */
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

/* Grille principale : Fixée à 2 colonnes pour un alignement 2x2 parfait */
.services-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 30px;
}

/* Nouvelle structure de carte épurée et professionnelle */
.service-card {
  background: #ffffff;
  border-radius: 20px;
  padding: 35px 30px;
  text-align: left;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.04);
  border: 1px solid #f1f5f9;
  transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
}

/* Conteneur de l'icône réaliste */
.icon-wrapper {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 55px;
  height: 55px;
  background-color: #eff6ff; /* Bleu très doux en arrière-plan */
  color: #2563eb; /* Couleur de l'icône vectorielle */
  border-radius: 14px;
  margin-bottom: 25px;
  transition: background-color 0.3s ease, color 0.3s ease;
}

/* Titres des services */
.service-card h3 {
  font-family: 'Times New Roman', Times, serif;
  font-size: 22px;
  font-weight: bold;
  color: #0f172a;
  margin-bottom: 12px;
}

/* Paragraphes en Arial simple, lisible et un peu gras */
.service-card p {
  font-family: Arial, sans-serif;
  font-weight: 550; /* Légèrement épaissi pour bien ressortir */
  font-size: 15px;
  color: #475569;
  line-height: 1.6;
  margin: 0;
}

/* Animations et interactions au survol */
.service-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(37, 99, 235, 0.08);
  border-color: #bfdbfe;
}

.service-card:hover .icon-wrapper {
  background-color: #2563eb;
  color: #ffffff; /* L'icône passe en blanc au survol */
}

/* --- TOUT LE RESPONSIVE (TABLETTE & MOBILE) --- */
@media (max-width: 768px) {
  .title h2 {
    font-size: 34px;
  }

  /* Passage à 1 colonne sur tablette et mobile pour un confort de lecture optimal */
  .services-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }
  
  .service-card {
    padding: 30px 20px; /* On réduit légèrement l'espace interne sur petit écran */
  }
}
</style>