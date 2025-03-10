<script setup>
    import "./Bouton.css";

    const props = defineProps({
        texteBouton: String,
        path: String
    })

</script>

<template>
    <div class="bouton relative inline-block">
        <div>
            <a :href="path">{{ texteBouton }}</a>
        </div>
    </div>
</template>