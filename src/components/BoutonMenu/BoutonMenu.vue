<script setup>
    import { ref} from 'vue'
    import './BoutonMenu.css'

    const props = defineProps({
        menuRef: {
            type: Object
        }
    })

    const btnActivate = ref(false)

    const toggleMenu = () => {
        if (!props.menuRef) return;

        const menu = props.menuRef

        if (!btnActivate.value) {
            menu.style.top = 0;
            menu.classList.replace("absolute", "fixed");

            btnActivate.value = true
        } else {
            menu.style.top = "-102vh";
            menu.classList.replace("fixed", "absolute");

            btnActivate.value = false
        }
    }

</script>

<template>
    <div class="hamburger fixed" @click="toggleMenu">
        <span v-for="n in 4" :id="`bar${ n }`"
        :class="[
            'bar',
            'block',
            'absolute',
            {
            'translate-right': btnActivate && n === 1,
            'rotate-45': btnActivate && n === 2,
            'rotate-minus-45': btnActivate && n === 3,
            'translate-left': btnActivate && n === 4
            }
        ]">
        </span>
    </div>
</template>