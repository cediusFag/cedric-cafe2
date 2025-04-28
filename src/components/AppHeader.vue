<script setup>
import { ref } from "vue";
import { RouterLink } from "vue-router";

const isMenuOpen = ref(false);

const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value;
};

const closeMenu = () => {
    isMenuOpen.value = false;
};
</script>

<template>
    <div>
        <div class="container h-[10vh] mx-auto flex items-center justify-between px-4 fixed top-0 left-0 z-1">
            
            <div class="text-white font-bold text-xl">
                <span>Logo</span>
                <!-- <img src="/images/logo.png" alt="Logo" class="h-8" /> -->
            </div>

            <div>
                <button @click="toggleMenu" class="text-black focus:outline-none" aria-label="Menu">
                    <span>menu</span>
                </button>
            </div>
        </div>

        <transition name="fade">
            <div v-if="isMenuOpen"
                class="fixed inset-0 z-50 flex justify-center bg-white/30 backdrop-blur-md transition-all">
                <div class="bg-white rounded-lg shadow-lg p-10 w-full flex flex-col items-center">
                    <div>
                        <RouterLink to="/">Home</RouterLink>
                    </div>
                    <div>
                        <RouterLink to="/menu">Menu</RouterLink>
                    </div>
                    <div>
                        <RouterLink to="/about">A propos</RouterLink>
                    </div>
                    <div>
                        <RouterLink to="/booking">Réservation</RouterLink>
                    </div>
                    <button @click="closeMenu" class="mt-6 text-gray-500 hover:text-gray-700 text-sm underline">
                        Fermer
                    </button>
                </div>
            </div>
        </transition>
    </div>
</template>

<style scoped>
    .fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>