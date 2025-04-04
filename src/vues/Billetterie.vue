<script setup>
    import AccueilContainer from './AccueilContainer.vue';
    import { billetterie } from '../data/crepuscule2025.json';

    const idTitreAccueilBilletterie = 'titre-billetterie';
    const titreAccueilBilletterie = billetterie.titre;
    const classes = 'flex-column start';
</script>
    
<template>
    <div id="billetterie" class="flex-column start">
        <AccueilContainer :id="idTitreAccueilBilletterie" :titre="titreAccueilBilletterie" :classes="classes" />
    </div>
</template>