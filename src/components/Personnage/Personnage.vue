<script setup>
    import personnage from "../../assets/images/personnage.png";
    import caillou1 from "../../assets/images/caillou_1.png";
    import caillou2 from "../../assets/images/caillou_2.png";
    import caillou3 from "../../assets/images/caillou_3.png";
    import caillou4 from "../../assets/images/caillou_4.png";
    import "./Personnage.css";
</script>

<template>
    <div id="scene" class="absolute">
        <img :src="personnage" class="absolute" id="personnage" />
        <img :src="caillou1" class="absolute" id="caillou-1" />
        <img :src="caillou2" class="absolute" id="caillou-2" />
        <img :src="caillou3" class="absolute" id="caillou-3" />
        <img :src="caillou4" class="absolute" id="caillou-4" />
    </div>
</template>
