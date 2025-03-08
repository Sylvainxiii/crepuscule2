<script setup>
    import { contact, info } from '/data/crepuscule2025.json'
    import logoFacebook from "/src/assets/images/facebook-f.svg";
    import logoInstagram from "/src/assets/images/instagram.svg";
    import logoEmail from "/src/assets/images/envelope.svg";
    import logoLocation from "/src/assets/images/location-dot.svg";
    import './FooterMobile.css'

    const linkFacebook = contact.facebook;
    const linkInstagram = contact.instagram;
    const linkEmail = contact.email;
    const linkMap = info.google_map;
</script>

<template>
    <div id="footer-mobile" class="flex-row center relative">
        <!-- Facebook -->
        <a :href="linkFacebook" aria-label="Facebook de Drac Events" target="_blank" class="fa-brands fa-facebook-f">
            <img :src="logoFacebook" alt="Facebook Logo" />
        </a>

        <!-- Instagram -->
        <a :href="linkInstagram" aria-label="Instagram de Drac Events" target="_blank" class="fa-brands fa-instagram">
            <img :src="logoInstagram" alt="Instagram Logo" />
        </a>

        <!-- Email -->
        <a :href="`mailto:${linkEmail}`" aria-label="Envoyer un mail à Drac Event">
            <img :src="logoEmail" alt="Email Logo" />
        </a>

        <!-- Localisation -->
        <a :href="linkMap" target="_blank" aria-label="Localiser Crépuscule Music Festival">
            <img :src="logoLocation" alt="Location Logo" />
        </a>
    </div>
</template>