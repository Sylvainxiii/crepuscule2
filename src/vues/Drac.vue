<script setup>
    import AccueilContainer from './AccueilContainer.vue';
    import { drac } from '../data/crepuscule2025.json';

    const idTitreAccueilDrac = 'titre-drac';
    const titreAccueilDrac = drac.titre;
    const classes = 'flex-column start';
</script>

<template>
    <div id="drac" class="flex-column start">
        <AccueilContainer :id="idTitreAccueilDrac" :titre="titreAccueilDrac" :classes="classes" />
    </div>
</template>