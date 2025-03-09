<script setup>
    import "./AccueilBilletterie.css";
    import Bouton from "/src/components/Bouton/Bouton.vue";
    import { billetterie, info } from "/data/crepuscule2025.json";

    const dates = info.dates;
    const titreAccueilBilletterie = billetterie.titre;
    const designation = billetterie.designation;
    const prix = billetterie.prix;
    const bouton = billetterie.bouton;
    const path = billetterie.path;
</script>

<template>
<div id="accueil-billetterie" class="flex-column space-between">
    <h1>{{ titreAccueilBilletterie }}</h1>
    <div id="grille-billetterie" class="grid">
    <div id="cellule-1-billetterie">{{ designation }}</div>
    <div id="cellule-2-billetterie">{{ dates }}</div>
    <div id="cellule-3-billetterie">{{ prix }}</div>
    </div>
    <Bouton :texteBouton="bouton" :path="path" />
</div>
</template>

