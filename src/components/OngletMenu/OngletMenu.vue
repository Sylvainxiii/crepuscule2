<script setup>
    import { computed } from 'vue'
    import pagesData from '/data/crepuscule2025.json'
    import './OngletMenu.css'

    const filteredPages = computed(() => {
        const result = {}

        for (const [key, value] of Object.entries(pagesData)){
            if (key !== 'footer') {
                result[key] = value
            }
        }
        return result
    })
</script>

<template>
    <ul id="liste-menu" class="flex-column">
        <li v-for="onglet of filteredPages" class="line-menu flex-row center">
            <a :href="onglet.path">{{ onglet.titre }}</a>
        </li>
    </ul>
</template>