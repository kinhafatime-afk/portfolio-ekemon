<template>
  <section id="hero" class="hero">
    <div class="content">
      <h1>Ekemon Carlos MONDOTE</h1>
      <h2>Community Manager</h2>
      <p>
        Gestion des réseaux sociaux, création de contenu
        et stratégie digitale.
      </p>
      <a
        href="https://wa.me/2290167223422"
        target="_blank"
        rel="noopener noreferrer"
        class="btn"
      >
        Me contacter
      </a>
    </div>
  </section>
</template>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: #ffffff;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, Times New Roman, serif;
  padding: 20px;
  box-sizing: border-box;

  background: linear-gradient(
      rgba(2, 0, 0, 0.25),
      rgba(0, 0, 0, 0.25)
    ),
    url('/images/commity.jpg');

  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment: fixed;
}

h1 {
  font-size: clamp(40px, 5vw, 70px);
  margin-bottom: 10px;
  line-height: 1.2;
  font-weight: 800;
  letter-spacing: -1px;
}

h2 {
  font-size: clamp(20px, 2.5vw, 32px);
  color: #3b82f6; /* Un bleu vif qui ressort magnifiquement sur le fond sombre */
  margin-bottom: 20px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1px;
}

p {
  font-size: clamp(16px, 1.5vw, 20px);
  color: #ffffff; /* Blanc cassé pour une lecture ultra-confortable */
  max-width: 600px;
  margin: 0 auto 35px auto;
  line-height: 1.6;
}

.btn {
  display: inline-block;
  padding: 15px 40px;
  border-radius: 50px;
  background: #3b82f6;
  color: #ffffff;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(59, 130, 246, 0.4);
}

/* Effet au survol du bouton */
.btn:hover {
  background: #2563eb;
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(59, 130, 246, 0.6);
}

.btn:active {
  transform: translateY(0);
}
</style>