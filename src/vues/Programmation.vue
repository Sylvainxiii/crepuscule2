<script setup>
    import AccueilContainer from "/src/components/AccueilContainer/AccueilContainer.vue";
    import { programmation } from "/data/crepuscule2025.json";

    const idTitreAccueilProgrammation = "titre-partenaires";
    const titreAccueilProgrammation = programmation.titre;
</script>

<template>
    <div id="partenaires" class="flex-column start">
        <AccueilContainer :id="idTitreAccueilProgrammation" :titre="titreAccueilProgrammation" />
    </div>
</template>