<script setup>
    import Personnage from '../Personnage/Personnage.vue'
    import "./Portail.css";
</script>

<template>
    <div id="portail" class="relative">
        <div id="face-dessus-ombre" class="relative">
            <div id="face-dessus" class="relative"></div>
        </div>
        <div id="face-gauche" class="absolute"></div>
        <div id="face-droite" class="absolute"></div>
        <div id="face-arriere" class="relative"></div>
        <Personnage />
    </div>
</template>