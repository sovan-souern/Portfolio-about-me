<template>
  <nav class="fixed w-full top-0 z-50 bg-white/95 backdrop-blur-md border-b border-gray-200 shadow-sm">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center py-4">
        <!-- Logo -->
        <div class="flex items-center">
          <div class="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center mr-3">
            <span class="text-white font-bold text-lg">SV</span>
          </div>
          <span class="text-xl font-bold text-gray-900">Sovan Souern</span>
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex space-x-8">
          <button v-for="item in navigation" :key="item.id" @click="scrollToSection(item.id)" :class="[
            'px-4 py-2 rounded-lg text-sm font-medium transition-all duration-300',
            activeSection === item.id
              ? 'bg-blue-600 text-white shadow-lg'
              : 'text-gray-600 hover:text-blue-600 hover:bg-gray-50'
          ]">
            {{ item.name }}
          </button>
        </div>

        <!-- Mobile Menu Button -->
        <div class="md:hidden">
          <button @click="mobileMenuOpen = !mobileMenuOpen"
            class="text-gray-600 hover:text-blue-600 p-2 rounded-lg hover:bg-gray-50 transition-colors duration-200">
            <span v-if="!mobileMenuOpen" class="text-xl">☰</span>
            <span v-else class="text-xl">✕</span>
          </button>
        </div>
      </div>

      <!-- Mobile Menu -->
      <div v-show="mobileMenuOpen" class="md:hidden pb-4 border-t border-gray-200 mt-4">
        <div class="space-y-2 pt-4">
          <button v-for="item in navigation" :key="item.id" @click="scrollToSection(item.id); mobileMenuOpen = false"
            :class="[
              'block w-full text-left px-4 py-3 rounded-lg text-sm font-medium transition-all duration-300',
              activeSection === item.id
                ? 'bg-blue-600 text-white'
                : 'text-gray-600 hover:text-blue-600 hover:bg-gray-50'
            ]">
            {{ item.name }}
          </button>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const activeSection = ref('home')
const mobileMenuOpen = ref(false)

const navigation = [
  { id: 'home', name: 'Home' },
  { id: 'about', name: 'About' },
  { id: 'skills', name: 'Skills' },
  { id: 'services', name: 'Services' },
  { id: 'portfolio', name: 'Portfolio' },
  { id: 'contact', name: 'Contact' }
]

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const handleScroll = () => {
  const sections = navigation.map(nav => nav.id)
  const scrollPosition = window.scrollY + 100

  for (const sectionId of sections) {
    const element = document.getElementById(sectionId)
    if (element) {
      const offsetTop = element.offsetTop
      const offsetHeight = element.offsetHeight
      if (scrollPosition >= offsetTop && scrollPosition < offsetTop + offsetHeight) {
        activeSection.value = sectionId
        break
      }
    }
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>