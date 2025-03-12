<script setup>

import './VueTitre.css';

const props = defineProps({
titre: {
    type: String,
    required: true
}
});
</script>

<template>
<div class="titre-container relative">
    <h1>{{ titre }}</h1>
</div>
</template>
