<script setup>
  import Background from './components/Background/Background.vue';
  import Navbar from './components/Navbar/Navbar.vue';
  import FooterPc from './components/FooterPc/FooterPc.vue';
  import FooterMobile from './components/FooterMobile/FooterMobile.vue';
  import Accueil from './vues/Accueil.vue';
</script>

<template>
    <Background />
    <Navbar />
    <div id = 'vue' class="flex-column center">
      <Accueil />
    </div>
    <FooterPc />
    <FooterMobile />
</template>

