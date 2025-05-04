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
        <section v-for="(section, index) in sections" :key="index" class="section"
            :style="{ backgroundColor: section.color }">
            <picture>
      <!-- Vidéo -->
      <video
        autoplay
        loop
        muted
        playsinline
        class="absolute top-0 left-0 w-full h-full object-cover"
        :poster="'/images/ton-image-de-fallback.jpg'"
      >
        <source src="/Madame Zouzoua VS Ministre des Économie et des Finances.mp4" type="video/mp4" />
        <!-- Option pour d'autres formats vidéo -->
        <!-- <source src="/videos/ton-fichier-video.webm" type="video/webm" /> -->
        <!-- Si la vidéo ne se charge pas, on affiche l'image -->
        <img src="/169788.jpg" alt="Fallback Image" />
      </video>
    </picture>

    <!-- Contenu au-dessus de la vidéo -->
    <div class="relative z-10 flex flex-col items-center justify-center h-full text-white text-center">
      <h2 class="mt-4 text-lg">{{ section.title }}</h2>
    </div>

    <!-- Optionnel: Overlay sombre -->
    <div class="absolute top-0 left-0 w-full h-full bg-black/50 z-0"></div>
    </section>
    </div>
</template>

<style scoped>
/* #scroll-container {
  height: 100%;
  scroll-behavior: smooth;
  overflow-x: hidden;
  scroll-snap-type: y mandatory;
} */

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