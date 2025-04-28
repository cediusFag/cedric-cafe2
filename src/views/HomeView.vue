<script setup>
    import { ref, onMounted } from "vue";
    const loading = ref(true);

    // Contenu et couleur de chaque section
    const sections = [
        { title: 'Section 1', color: '#3498db' },
        { title: 'Section 2', color: '#e67e22' },
        { title: 'Section 3', color: '#2ecc71' },
        { title: 'Section 4', color: '#9b59b6' },
    ];

    onMounted(() => {
      setTimeout(() => {
        loading.value = false;
      }, 2000);
    });
</script>

<template>
    <div id="scroll-container">
        <div v-for="(section, index) in sections" :key="index" class="section"
            :style="{ backgroundColor: section.color }">
            {{ section.title }}
        </div>
    </div>
</template>

<style scoped>
#scroll-container {
  height: 100%;
  scroll-behavior: smooth;
  overflow-x: hidden;
  scroll-snap-type: y mandatory;
}

.section {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 3rem;
    color: white;
    position: relative;
    transition: transform 1s ease-out;
    scroll-snap-align: start;
}

.section:nth-child(1) {
    background: #3498db;
}

.section:nth-child(2) {
    background: #e67e22;
}

.section:nth-child(3) {
    background: #2ecc71;
}

.section:nth-child(4) {
    background: #9b59b6;
}
</style>