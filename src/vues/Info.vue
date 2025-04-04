<script setup>
    import VueTitre from "/src/components/VueTitre/VueTitre.vue";
    import VueContainer from "/src/components/VueContainer/VueContainer.vue";
    import { info } from "/data/crepuscule2025.json";
    import VueDeroulant from "../components/VueDeroulant/VueDeroulant.vue";

    const page = info.page;
    const titreInfo = info.titre;
</script>

<template>
    <div>
        <VueTitre :titre="titreInfo" id="info" class="flex-column start" />
        <VueContainer>
            <div v-for="(contenuParagraphe, paragraphe) in page" :key="paragraphe" :id="paragraphe">
                <h2>{{ contenuParagraphe.titreh2 }}</h2>
                <div v-for="(contenu, elmt) in contenuParagraphe" :key="elmt">
                    <div v-if="elmt !== 'titreh2' && elmt !== 'faq'">
                        {{ contenu }}
                    </div>
                    <div v-else-if="elmt === 'faq'">
                        <VueDeroulant
                            v-for="(faqItem, question) in contenu"
                            :key="question"
                            :contenuVisible="faqItem.question"
                            :contenuCache="faqItem.reponse"
                            :id="question"
                        />
                    </div>
                </div>
            </div>
        </VueContainer>
    </div>
</template>
