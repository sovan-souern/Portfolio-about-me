<template>
  <div class="services-view py-20">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-20">
        <h1 class="text-5xl md:text-6xl font-bold mb-6">My Services</h1>
        <div class="w-24 h-1 bg-gradient-to-r from-blue-400 to-purple-600 mx-auto mb-8"></div>
        <p class="text-xl text-gray-400 max-w-3xl mx-auto">
          Comprehensive digital solutions tailored to your business needs
        </p>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="service in services" 
          :key="service.id"
          class="bg-gray-900 p-8 rounded-xl hover:bg-gray-800 transition-all duration-300 transform hover:-translate-y-2 hover:shadow-2xl"
        >
          <div class="w-16 h-16 bg-gradient-to-r from-blue-500 to-purple-600 rounded-lg flex items-center justify-center mb-6">
            <span class="text-2xl">{{ service.icon }}</span>
          </div>
          <h3 class="text-2xl font-bold mb-4 text-blue-400">{{ service.title }}</h3>
          <p class="text-gray-400 mb-6 leading-relaxed">{{ service.description }}</p>
          <div class="text-3xl font-bold text-purple-400 mb-4">{{ service.price }}</div>
          <button class="w-full bg-gradient-to-r from-blue-600 to-purple-600 text-white py-3 rounded-lg hover:from-blue-700 hover:to-purple-700 transition-all duration-300 font-semibold">
            Get Started
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const services = ref([
  {
    id: 1,
    title: 'Web Development',
    description: 'Custom web applications built with modern frameworks and best practices.',
    icon: '💻',
    price: 'From $2,500'
  },
  {
    id: 2,
    title: 'Mobile App Development',
    description: 'Native and cross-platform mobile applications for iOS and Android.',
    icon: '📱',
    price: 'From $5,000'
  },
  {
    id: 3,
    title: 'UI/UX Design',
    description: 'User-centered design solutions that enhance user experience and engagement.',
    icon: '🎨',
    price: 'From $1,500'
  }
])
</script>