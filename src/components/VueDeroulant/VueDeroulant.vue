<script setup>
    import { ref } from 'vue';
    import "./VueDeroulant.css";

    const props = defineProps({
        contenuVisible: String,
        contenuCache: String,
        id: String,
    });

    const isExpanded = ref(false);

    const toggleExpand = () => {
        isExpanded.value = !isExpanded.value;
    };
</script>

<template>
    <div :class="['deroulant', { deroule: isExpanded }]" :id="id" @click="toggleExpand">
        <div class="deroulant-visible">{{ contenuVisible }}</div>
        <div class="deroulant-cache" :style="{ height: isExpanded ? 'auto' : '0px', marginBottom: isExpanded ? '2em' : '0em' }">
            <div v-html="contenuCache"></div>
        </div>
    </div>
</template>

