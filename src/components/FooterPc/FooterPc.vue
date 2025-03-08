<script setup>
    import { contact, footer, info } from '/data/crepuscule2025.json'
    import logoFacebook from "/src/assets/images/facebook-f.svg";
    import logoInstagram from "/src/assets/images/instagram.svg";
    import './FooterPc.css'

    const linkFacebook = contact.facebook;
    const linkInstagram = contact.instagram;
    const linkEmail = contact.email;
    const titreReseau = footer.reseauh2;
    const titreContact = footer.contacth2;
    const titreAcces = footer.accesh2;
    const lieux = info.lieux;
    const rue = info.rue;
    const codePostal = info.CP;
    const ville = info.ville;
    const mapFooter = info.google_map;
</script>

<template>
    <div id="footer" class="flex-row space-between-top relative">
        <!-- Volet réseaux sociaux -->
        <div id="social-footer" class="flex-column start">
            <h2>{{ titreReseau }}</h2>
            <div class="flex-row space-between">
                <a :href="linkFacebook" aria-label="Facebook de Drac Events" target="_blank" class="fa-brands fa-facebook-f">
                    <img :src="logoFacebook" alt="Facebook Logo" />
                </a>
                <a :href="linkInstagram" aria-label="Instagram de Drac Events" target="_blank" class="fa-brands fa-instagram">
                    <img :src="logoInstagram" alt="Instagram Logo" />
                </a>
            </div>
        </div>

        <!-- Volet Contact -->
        <div id="contact-footer" class="flex-column center">
            <h2>{{ titreContact }}</h2>
            <a :href="`mailto:${linkEmail}`" aria-label="Envoyer un mail à Drac Event">{{ linkEmail }}</a>
        </div>

        <!-- Volet Accès Festival -->
        <div id="acces-footer" class="flex-column start">
            <a :href="mapFooter" target="_blank" aria-label="Localiser Crépuscule Music Festival">
                <h2>{{ titreAcces }}</h2>
                <div id="adresse-footer" class="flex-column start">
                    <p>{{ lieux }}</p>
                    <p>{{ rue }}</p>
                    <p>{{ codePostal }} {{ ville }}</p>
                </div>
            </a>
        </div>
    </div>
</template>