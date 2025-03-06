<script setup>
    import { ref, onMounted, onUnmounted } from 'vue'
    import backgroundImage from '/src/assets/images/fond-body.webp'
    import './Background.css'

    const background = ref(null)
    let lastScrollY = 0
    let app = null

    // Fonction qui gère l'effet parallaxe
const handleScroll = () => {
    //const app = document.querySelector('.app')
    const scrollY = app.scrollTop
    const windowHeight = window.innerHeight
    
    if (background.value) {
    // Obtenir le positionnement de la div par rapport à la fenêtre
    const backgroundRect = background.value.getBoundingClientRect()
    
    // Calculer la position du bas et du haut de la div par rapport à la fenêtre
    const backgroundBottom = backgroundRect.bottom
    const backgroundTop = backgroundRect.top
    
    // Détecter le sens du défilement
    const direction = (scrollY > lastScrollY) ? 'down' : 'up'
    
    // Si le bas de l'élément est encore au-dessous du bas de la fenêtre, continue de bouger
    if (backgroundBottom - 20 > windowHeight) {
        background.value.style.top = (-scrollY / 3) + 'px'
    } else if (direction === 'up') {
        if (-scrollY >= backgroundTop * 3) {
            background.value.style.top = (-scrollY / 3) + 'px'
        }
    }
    
    // Mettre à jour la position précédente de défilement
    lastScrollY = scrollY
    }
}

// Ajouter l'écouteur d'événement au montage du composant
onMounted(() => {
    app = document.querySelector('#app')
    if (app) {
        app.addEventListener('scroll', handleScroll)
    } 
})

// Nettoyer l'écouteur d'événement au démontage du composant
onUnmounted(() => {
    if (app) {
        app.removeEventListener('scroll', handleScroll)
        app = null // Libère la référence
    }
})
</script>

<template>
    <div class="background" ref="background">
        <img class="background-img" :src="backgroundImage" alt="Background">
    </div>
</template>