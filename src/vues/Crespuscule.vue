<script setup>
    import VueContainer from "/src/components/VueContainer/VueContainer.vue";
    import VueTitre from "/src/components/VueTitre/VueTitre.vue";
    import { crepuscule } from "/data/crepuscule2025.json";

    const page = crepuscule.page;
    const titreAccueilInfo = page.titreh1;

  // Filtrer les sections pour exclure "titreh1"
    const sections = Object.keys(page)
        .filter(key => key !== "titreh1")
        .reduce((obj, key) => {
        obj[key] = page[key];
        return obj;
        }, {});
</script>

<template>
    <div>
        <VueTitre :titre="titreAccueilInfo" class="flex-column center" />
        <VueContainer class="texte-centre">
        <div v-for="(section, paragraphe) in sections" :key="paragraphe" :id="paragraphe">
            <h2>{{ section.titreh2 }}</h2>
            <p v-html="section.paragraphe"></p>
        </div>
        </VueContainer>
    </div>
</template>