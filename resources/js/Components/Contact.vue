<template>
<section id="contact">

    <div class="container">

        <div class="title">
            <h2>Contactez-moi</h2>
            <p>Parlons de votre projet.</p>
        </div>

        <div class="contact-wrapper">

            <div class="contact-info">

                <h3>Disponible pour vos projets</h3>

                <p>
                    Vous souhaitez développer votre visibilité,
                    améliorer votre communication ou booster vos ventes ?
                </p>

                <div class="info-card">
                    <svg class="icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path></svg>
                    <span>WhatsApp : +229 01 67 22 34 22</span>
                </div>

                <div class="info-card">
                    <svg class="icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path><polyline points="22,6 12,13 2,6"></polyline></svg>
                    <span>ekemoncarlo@gmail.com</span>
                </div>

                <div class="info-card">
                    <svg class="icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path><circle cx="12" cy="10" r="3"></circle></svg>
                    <span>Parakou, Bénin</span>
                </div>

            </div>

            <form @submit.prevent="sendWhatsApp">

                <input
                    v-model="form.nom"
                    type="text"
                    placeholder="Nom complet"
                    required
                >

                <input
                    v-model="form.telephone"
                    type="tel"
                    inputmode="numeric"
                    pattern="[0-9]*"
                    placeholder="Téléphone"
                    required
                    @input="form.telephone = form.telephone.replace(/\D/g, '')"
                >

                <input
                    v-model="form.email"
                    type="email"
                    placeholder="Adresse email"
                    required
                >

                <select v-model="form.service" required>

                    <option value="" disabled selected>
                        Choisissez un service
                    </option>

                    <option value="Gestion Réseaux Sociaux">
                        Gestion Réseaux Sociaux
                    </option>

                    <option value="Création de Contenu">
                        Création de Contenu
                    </option>

                    <option value="Publicité Meta Ads">
                        Publicité Meta Ads
                    </option>

                    <option value="Stratégie Digitale">
                        Stratégie Digitale
                    </option>

                </select>

                <textarea
                    v-model="form.message"
                    rows="5"
                    placeholder="Votre message..."
                ></textarea>

                <button type="submit">
                    Envoyer sur WhatsApp
                </button>

            </form>

        </div>

    </div>

</section>
</template>

<script setup>
import { reactive } from 'vue'

const form = reactive({
    nom:'',
    telephone:'',
    email:'',
    service:'',
    message:''
})

const sendWhatsApp = () => {
    const numero = '2290167223422'
    const texte = `
NOUVELLE DEMANDE

Nom : ${form.nom}
Téléphone : ${form.telephone}
Email : ${form.email}
Service : ${form.service}

Message :
${form.message}
`
    const url = `https://wa.me/${numero}?text=${encodeURIComponent(texte)}`
    window.open(url,'_blank')
}
</script>

<style scoped>
/* On s'assure que toute la section a le fond bleu sombre */
#contact {
    padding: 100px 8%;
    background-color: #0f172a; /* Bleu sombre (Slate 900) */
    color: white;
}

.title h2 {
    font-size: 2.5rem;
    margin-bottom: 10px;
}

.title p {
    color: #94a3b8;
    margin-bottom: 40px;
}

.contact-wrapper {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
}

.contact-info {
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.contact-info h3 {
    font-size: 2rem;
}

.contact-info p {
    color: #cbd5e1;
    line-height: 1.8;
}

/* Cartes d'info stylisées et réalistes */
.info-card {
    display: flex;
    align-items: center;
    gap: 15px;
    padding: 20px;
    border-radius: 15px;
    background: rgba(255, 255, 255, .05);
    border: 1px solid rgba(255, 255, 255, .08);
}

.icon {
    width: 24px;
    height: 24px;
    color: #3b82f6; /* Couleur bleue accentuée pour les icônes */
}

form {
    display: flex;
    flex-direction: column;
    gap: 15px;
}

input,
textarea {
    background: rgba(255, 255, 255, .05);
    border: 1px solid rgba(255, 255, 255, .08);
    padding: 15px;
    border-radius: 15px;
    color: white;
    font-family: inherit;
}

/* --- AJUSTEMENT DE LA ZONE SERVICE (SELECT) --- */
select {
    background-color: #ffffff;   /* Fond blanc pour la clarté */
    color: #0f172a;              /* Écritures en bleu sombre très foncé pour être lisibles */
    border: 1px solid #cbd5e1;
    padding: 15px;
    border-radius: 15px;
    font-family: inherit;
    font-size: 1rem;
    cursor: pointer;
}

/* Style des options à l'intérieur du select */
select option {
    background-color: #ffffff;
    color: #0f172a;
}

/* Style spécifique pour l'option désactivée "Choisissez un service" */
select option:disabled {
    color: #94a3b8;
}

button {
    border: none;
    padding: 16px;
    border-radius: 15px;
    cursor: pointer;
    font-weight: bold;
    background: linear-gradient(90deg, #3b82f6, #8b5cf6);
    color: white;
    transition: opacity 0.2s ease;
}

button:hover {
    opacity: 0.9;
}

@media(max-width:768px){
    .contact-wrapper {
        grid-template-columns: 1fr;
    }
}
</style>