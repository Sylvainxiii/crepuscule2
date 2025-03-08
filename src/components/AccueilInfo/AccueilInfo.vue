<script setup>
    import Bouton from "../Bouton/Bouton.vue";
    import { crepuscule } from "/data/crepuscule2025.json";
    import "./AccueilInfo.css";

    const titreAccueilInfo = crepuscule.titre;
    const titreh2 = crepuscule.titreh2;
    const texteAccueilInfo = crepuscule.texte;
    const boutonAccueilInfo = crepuscule.bouton;
    const path = crepuscule.path;
</script>

<template>
    <div id="accueil-info" class="flex-column center">
        <h1 id="titre-accueil-info">{{ titreAccueilInfo }}</h1>
        <h2 id="titreh2-accueil-info">{{ titreh2 }}</h2>
        <div id="texte-accueil-info" class="texte-centre" v-html="texteAccueilInfo"></div>
        <Bouton :texteBouton="boutonAccueilInfo" :path="path"/>
    </div>
</template>