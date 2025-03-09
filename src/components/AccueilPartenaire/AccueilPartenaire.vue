<script setup>
    import { ref, onMounted, onBeforeUnmount } from 'vue';
    import "./AccueilPartenaires.css";
    import { partenaires } from "/data/crepuscule2025.json";

    const logoPartenaires = Object.fromEntries(
        Object.entries(import.meta.glob("/src/assets/images/partenaires/*.svg", { eager: true, import: "default" })).map(([path, module]) => {
            const filename = path.split("/").pop();
            return [filename, module];
        })
    );

    const titreAccueilPartenaires = partenaires.titre;
    // Génére une liste de logo initiale en choisissant au hasard le logo central
    const listeLogoInitial = ref(getLogos(partenaires.liste, Math.floor(Math.random() * Object.keys(partenaires.liste).length)));

    // Determine une liste de logo en prenant comme point de départ le logo central puis les 3 precédents et les 3 suivants tous les autres auront une classe standard
    function getLogos(liste, index) {
        const longueurListe = Object.keys(liste).length;
        let result = [];
        for (let i = 3; i >= 1; i--) {
            result.push(liste[(index - i + longueurListe) % longueurListe]);
        }
        result.push(liste[index]);
        for (let i = 1; i < longueurListe - 3; i++) {
            result.push(liste[(index + i) % longueurListe]);
        }
        return result;
    }

    // Assigne les classes spécifiques au 7 logos de la liste définie, les autres étant assigné d'une classe standard
    function getLogoClass(index) {
        if (index === 3) {
            return "logo-centre";
        } else if ([1, 2, 4, 5].includes(index)) {
            return "logo-voisin-" + index;
        } else if (index === 0) {
            return "logo-hidden-gauche";
        } else if (index === 6) {
            return "logo-hidden-droite";
        } else {
            return "hidden-logo";
        }
    }

    let animationInterval;

    const animateLogos = () => {
        const logosContainer = document.getElementById("ligne-partenaire");
        if (!logosContainer) return;

        const logos = Array.from(logosContainer.getElementsByClassName("logo-partenaire-accueil"));

        const shiftLogos = () => {
            let previousClass = "hidden-logo";
            logos.forEach((logo) => {
                const currentClasses = logo.classList;
                const currentClass = currentClasses[1];
                logo.classList.replace(currentClass, previousClass);
                previousClass = currentClass;
            });
            const firstLogo = logos[0];
            logosContainer.removeChild(firstLogo);
            logosContainer.appendChild(firstLogo);
            logos.push(logos.shift());
        };

        const ANIMATION_INTERVAL = 2000;
        animationInterval = setInterval(shiftLogos, ANIMATION_INTERVAL);

        const observer = new IntersectionObserver((entries) => {
            entries.forEach((entry) => {
                if (!entry.isIntersecting) {
                    clearInterval(animationInterval);
                } else {
                    animationInterval = setInterval(shiftLogos, ANIMATION_INTERVAL);
                }
            });
        });

        observer.observe(logosContainer);

        return () => {
            clearInterval(animationInterval);
            observer.disconnect();
        };
    };

    onMounted(() => {
        setTimeout(() => {
            animateLogos();
        }, 100);
    });

    onBeforeUnmount(() => {
        clearInterval(animationInterval);
    });
</script>

<template>
<div id="accueil-partenaires" class="flex-column start">
    <h1>{{ titreAccueilPartenaires }}</h1>
    <div id="ligne-partenaire" class="flex-row center">
        <img
            v-for="(logo, index) in listeLogoInitial"
            :key="index"
            :src="logoPartenaires[logo.logo]"
            :id="index.toString()"
            class="logo-partenaire-accueil"
            :class="getLogoClass(index)"
        />
    </div>
</div>
</template>
