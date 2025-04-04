<script setup>
    import AccueilContainer from './AccueilContainer.vue';
    import { contact } from '../data/crepuscule2025.json';

    const idTitreAccueilContact = 'titre-contact';
    const titreAccueilContact = contact.titre;
    const classes = 'flex-column start';
</script>

<template>
    <div id="contact" class="flex-column start">
        <AccueilContainer :id="idTitreAccueilContact" :titre="titreAccueilContact" :classes="classes" />
    </div>
</template>