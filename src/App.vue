<script setup>
  import Background from './components/Background/Background.vue';
  import Menu from './components/Menu/Menu.vue';
  import Footer from './components/Footer/Footer.vue';
  import FooterMobile from './components/FooterMobile/FooterMobile.vue';
</script>

<template>
    <Background />
    <Menu />
    <div id = 'foreground'>
    </div>
    <Footer />
    <FooterMobile />
</template>

