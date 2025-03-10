<script setup>
    import { ref, onMounted, onBeforeUnmount } from 'vue';
    import * as THREE from 'three';
    import { GLTFLoader } from 'three/addons/loaders/GLTFLoader.js';
    
    const props = defineProps({
        couleur: {
        type: String,
        required: true
        }
    });
    
    const container = ref(null);
    let scene, renderer, camera, artefact, axis;
    
    function updateSize() {
        if (renderer && camera && container.value) {
            renderer.setSize(container.value.clientWidth, container.value.clientHeight);
            camera.aspect = container.value.clientWidth / container.value.clientHeight;
            camera.updateProjectionMatrix();
        }
    }
    
    function animate() {
        if (renderer && scene && camera && artefact && axis) {
            render(renderer, scene, camera, artefact, axis);
            requestAnimationFrame(animate);
        }
    }
    
    function init() {
        // Scene
        scene = new THREE.Scene();
    
        // Renderer
        renderer = new THREE.WebGLRenderer({ antialias: true });
        renderer.setClearColor(0xffffff, 0);
        renderer.shadowMap.enabled = true;
        renderer.shadowMap.type = THREE.PCFSoftShadowMap;
        container.value.appendChild(renderer.domElement);
    
        // Lights
        const ambientLight = new THREE.AmbientLight(0xffffff, 0.8);
        scene.add(ambientLight);
    
        const dirLight = new THREE.PointLight(0xffffff, 100, 400, 1);
        dirLight.position.set(-2, 2, 3).multiplyScalar(100);
        dirLight.castShadow = true;
        dirLight.shadow.mapSize.width = 1024;
        dirLight.shadow.mapSize.height = 1024;
        dirLight.shadow.camera.near = 1;
        dirLight.shadow.camera.far = 500;
        dirLight.shadow.bias = -0.001;
        scene.add(dirLight);
    
        const dirLight2 = new THREE.DirectionalLight(props.couleur, 2);
        dirLight2.position.set(5, -2, 3).multiplyScalar(100);
        dirLight2.castShadow = true;
        dirLight2.shadow.mapSize.width = 1024;
        dirLight2.shadow.mapSize.height = 1024;
        dirLight2.shadow.camera.near = 1;
        dirLight2.shadow.camera.far = 500;
        dirLight2.shadow.bias = -0.001;
        scene.add(dirLight2);
    
        // Camera
        camera = new THREE.PerspectiveCamera(75, container.value.clientWidth / container.value.clientHeight, 1, 1000);
        camera.position.set(0, 0, container.value.clientWidth);
        camera.lookAt(new THREE.Vector3(0, 0, 0));
        scene.add(camera);
    
        axis = new THREE.Vector3(1, 2, 1.8).normalize();
    
        // Load GLTF model
        const loader = new GLTFLoader();
        loader.load(
            'test_cube.gltf',
            (gltf) => {
                artefact = gltf.scene;
                artefact.traverse((child) => {
                    if (child.isMesh) {
                        child.castShadow = true;
                        child.receiveShadow = true;
                    }
                });
        
                scene.add(artefact);
        
                const quaternion = new THREE.Quaternion();
                const up = new THREE.Vector3(0, 1, 0);
                quaternion.setFromUnitVectors(up, axis);
                artefact.applyQuaternion(quaternion);
        
                const scaleFactor = 150;
                artefact.scale.set(scaleFactor, scaleFactor, scaleFactor);
        
                updateSize();
                animate();
            },
            undefined,
            (error) => {
                console.error('Erreur de chargement du modèle GLTF:', error);
            }
        );
    }
    
    onMounted(() => {
        const resizeObserver = new ResizeObserver(() => {
            updateSize();
        });
        resizeObserver.observe(container.value);
    
        window.addEventListener('resize', updateSize);
    
        if (container.value.clientWidth > 0 && container.value.clientHeight > 0) {
            init();
        } else {
            const observer = new ResizeObserver((entries) => {
                if (container.value.clientWidth > 0 && container.value.clientHeight > 0) {
                    observer.disconnect();
                    init();
                }
            });
            observer.observe(container.value);
        }
    
        onBeforeUnmount(() => {
            resizeObserver.disconnect();
            window.removeEventListener('resize', updateSize);
        });
    });
    
    function render(renderer, scene, camera, artefact, axis) {
        const angle = 0.01;
        const quaternion = new THREE.Quaternion();
        quaternion.setFromAxisAngle(axis, angle);
        artefact.quaternion.multiplyQuaternions(quaternion, artefact.quaternion);
        renderer.render(scene, camera);
    }
</script>

<template>
    <div class="accueil-container relative flex-column center">
        <div ref="container" class="artefact-container"></div>
    </div>
</template>

<style scoped>
    .artefact-container {
        width: 100%;
        height: 100%;
    }
</style>