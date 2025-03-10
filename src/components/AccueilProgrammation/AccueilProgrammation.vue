<script setup>
    import { programmation } from '/data/crepuscule2025.json';
    import Artefact from '../Artefact/Artefact.vue';
    import './AccueilProgrammation.css';
    
    const titreAccueilProgrammation = programmation.titre;
    const artistes = programmation.artistes;
</script>  

<template>
    <div id="accueil-programmation" class="flex-column center">
        <h1>{{ titreAccueilProgrammation }}</h1>
        <div id="accueil-programmation-grille" class="grid">
            <Artefact
                v-for="(artiste, index) in artistes"
                :key="index"
                :couleur="artiste.couleur"
            />
        </div>
    </div>
</template>
