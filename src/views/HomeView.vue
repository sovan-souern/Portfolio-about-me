<template>
  <div class="home-view">
    <!-- Hero Section -->
    <section class="min-h-screen flex items-center justify-center bg-gradient-to-br from-black via-gray-900 to-black">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <div class="animate-fade-in-up">
          <h1 class="text-5xl md:text-7xl font-bold mb-6">
            Welcome to My 
            <span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-purple-600">
              Portfolio
            </span>
          </h1>
          
          <p class="text-xl md:text-2xl text-gray-300 mb-8 font-light">
            Full Stack Developer & Creative Designer
          </p>
          
          <p class="text-lg text-gray-400 mb-12 max-w-3xl mx-auto leading-relaxed">
            I create exceptional digital experiences through innovative web development, 
            stunning UI/UX design, and cutting-edge technology solutions.
          </p>
          
          <div class="flex flex-col sm:flex-row gap-6 justify-center">
            <router-link 
              to="/portfolio" 
              class="bg-gradient-to-r from-blue-600 to-purple-600 text-white px-8 py-4 rounded-lg hover:from-blue-700 hover:to-purple-700 transition-all duration-300 font-semibold shadow-lg hover:shadow-xl transform hover:-translate-y-1"
            >
              View My Work
            </router-link>
            <router-link 
              to="/contact" 
              class="border-2 border-blue-500 text-blue-400 px-8 py-4 rounded-lg hover:bg-blue-500 hover:text-white transition-all duration-300 font-semibold"
            >
              Get In Touch
            </router-link>
          </div>
        </div>
      </div>
    </section>

    <!-- Quick Stats -->
    <section class="py-20 bg-gray-900/50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8 text-center">
          <div v-for="stat in stats" :key="stat.label" class="p-6">
            <div class="text-4xl md:text-5xl font-bold text-blue-400 mb-2">{{ stat.value }}</div>
            <div class="text-gray-400 font-medium">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const stats = ref([
  { value: '50+', label: 'Projects Completed' },
  { value: '5+', label: 'Years Experience' },
  { value: '30+', label: 'Happy Clients' },
  { value: '24/7', label: 'Support' }
])
</script>

<style scoped>
@keyframes fade-in-up {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in-up {
  animation: fade-in-up 1s ease-out;
}
</style>