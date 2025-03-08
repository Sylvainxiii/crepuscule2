<script setup>
import './Banniere.css';
import Portail from '/src/components/Portail/Portail.vue';
import logo from "/src/assets/images/logo_crepuscule.svg";
import { info } from "/data/crepuscule2025.json";

const dateLieu = `${info.ville} - ${info.dates}`;
</script>

<template>
    <div id="banniere" class="flex-column start">
        <img :src="logo" alt="Crepuscule Music Festival logo" id="logo-banniere" />
        <h1 id="date-lieu-banniere">{{ dateLieu }}</h1>
        <Portail />
    </div>
</template>