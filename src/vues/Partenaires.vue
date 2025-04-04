<script setup>
    import AccueilContainer from "/src/components/AccueilContainer/AccueilContainer.vue";
    import { partenaires } from "/data/crepuscule2025.json";

    const idTitreAccueilPartenaires = "titre-partenaires";
    const titreAccueilPartenaires = partenaires.titre;
</script>

<template>
    <div id="partenaires" class="flex-column start">
        <AccueilContainer :id="idTitreAccueilPartenaires" :titre="titreAccueilPartenaires" />
    </div>
</template>

