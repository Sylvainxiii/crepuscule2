<script setup>
import VueTitre from "/src/components/VueTitre/VueTitre.vue";
import VueContainer from "/src/components/VueContainer/VueContainer.vue";
import { engagements } from "/data/crepuscule2025.json";

const page = engagements.page;
const titreEngagements = page.titreh1;
const epilogue = page.epilogue;

// Filtrer les sections pour exclure "titreh1"
const sections = Object.keys(page)
    .filter(key => key !== "titreh1" && key !== "epilogue")
    .reduce((obj, key) => {
        obj[key] = page[key];
        return obj;
    }, {});
</script>

<template>
    <div>
        <VueTitre :titre="titreEngagements" class="flex-column center" />
        <VueContainer class="texte-centre">
            <p v-html="epilogue"></p>
            <div v-for="(section, paragraphe) in sections" :key="paragraphe" :id="paragraphe">
                <h2>{{ section.titreh2 }}</h2>
                <div v-for="(contenu, liste) in section" :key="liste">
                    <div v-if="liste.indexOf('liste') === 0">
                        <h3>{{ contenu.titreh3 }}</h3>
                        <ul>
                            <li v-for="(ligne, index) in contenu" :key="index" v-if="index !== 'titreh3'">
                                {{ ligne }}
                            </li>
                        </ul>
                    </div>
                    <p v-else-if="liste === 'paragraphe'" v-html="contenu"></p>
                </div>
            </div>
        </VueContainer>
    </div>
</template>
