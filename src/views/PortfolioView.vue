<template>
  <div class="portfolio-view py-20">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-20">
        <h1 class="text-5xl md:text-6xl font-bold mb-6">My Portfolio</h1>
        <div class="w-24 h-1 bg-gradient-to-r from-blue-400 to-purple-600 mx-auto mb-8"></div>
        <p class="text-xl text-gray-400 max-w-3xl mx-auto">
          A showcase of my latest projects and creative solutions
        </p>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="project in projects" 
          :key="project.id" 
          class="group bg-gray-900 rounded-xl overflow-hidden hover:bg-gray-800 transition-all duration-300 transform hover:-translate-y-2 hover:shadow-2xl"
        >
          <img :src="project.image" :alt="project.title" class="w-full h-64 object-cover group-hover:scale-110 transition-transform duration-300">
          <div class="p-6">
            <h3 class="text-xl font-semibold mb-2 group-hover:text-blue-400 transition-colors">{{ project.title }}</h3>
            <p class="text-gray-400 mb-4">{{ project.description }}</p>
            <div class="flex flex-wrap gap-2">
              <span v-for="tech in project.technologies" :key="tech" class="px-3 py-1 bg-blue-500/20 text-blue-400 text-sm rounded-full">
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const projects = ref([
  {
    id: 1,
    title: 'E-Commerce Platform',
    description: 'Modern e-commerce solution with advanced features',
    image: 'https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?w=400&h=300&fit=crop',
    technologies: ['Vue.js', 'Node.js', 'MongoDB']
  },
  {
    id: 2,
    title: 'Task Management App',
    description: 'Collaborative productivity application',
    image: 'https://images.unsplash.com/photo-1611224923853-80b023f02d71?w=400&h=300&fit=crop',
    technologies: ['React', 'Express', 'PostgreSQL']
  },
  {
    id: 3,
    title: 'Weather Dashboard',
    description: 'Real-time weather tracking system',
    image: 'https://images.unsplash.com/photo-1504608524841-42fe6f032b4b?w=400&h=300&fit=crop',
    technologies: ['Vue.js', 'Chart.js', 'API']
  }
])
</script>