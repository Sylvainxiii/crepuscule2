<script setup>
    import { ref } from 'vue';
    import BoutonMenu from '../BoutonMenu/BoutonMenu.vue';
    import OngletMenu from '../OngletMenu/OngletMenu.vue';
    import './Navbar.css'

    const menuElement = ref(null)

</script>

<template>
    <div id='menu' ref='menuElement' class='flex-column center absolute'>
        <OngletMenu />
    </div>
    <BoutonMenu :menuRef='menuElement'/>
</template>