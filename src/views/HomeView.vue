<template>
  <section id="home" class="min-h-screen flex items-center relative overflow-hidden bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full relative z-10">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
        <div class="text-center lg:text-left">
          <div class="mb-6">
            <span class="inline-block px-4 py-2 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mb-4">
              Welcome to my portfolio
            </span>
          </div>
          <h1 class="text-5xl md:text-7xl font-bold mb-6 leading-tight text-gray-900">
            Hi, I'm <span class="text-blue-600">Sovan Souern</span>
          </h1>
          <p class="text-xl md:text-2xl mb-8 text-gray-600 leading-relaxed">
            Web Developer crafting exceptional digital experiences with modern technologies
          </p>
          <div class="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start mb-8">
            <button @click="scrollToSection('skills')" class="bg-blue-600 text-white px-8 py-4 rounded-lg font-semibold text-lg hover:bg-blue-700 transition-all duration-300 transform hover:scale-105 shadow-lg">
              View My Skills
            </button>
            <button @click="scrollToSection('contact')" class="border-2 border-blue-600 text-blue-600 px-8 py-4 rounded-lg font-semibold text-lg hover:bg-blue-600 hover:text-white transition-all duration-300">
              Get In Touch
            </button>
          </div>
          <div class="flex justify-center lg:justify-start space-x-6">
            <a href="#" class="text-gray-400 hover:text-blue-600 transition-colors duration-200">GitHub</a>
            <a href="#" class="text-gray-400 hover:text-blue-600 transition-colors duration-200">LinkedIn</a>
            <a href="#" class="text-gray-400 hover:text-blue-600 transition-colors duration-200">Twitter</a>
            <a href="#" class="text-gray-400 hover:text-blue-600 transition-colors duration-200">Email</a>
          </div>
        </div>
        <div class="flex justify-center">
          <div class="relative">
            <div class="w-80 h-80 rounded-full bg-gradient-to-br from-blue-100 to-blue-300 via-blue-200 border-4 border-blue-600 shadow-xl hover:shadow-2xl transition-shadow duration-300 flex items-center justify-center transform hover:-translate-y-2 hover:rotate-1">
              <div class="w-72 h-72 rounded-full bg-white flex items-center justify-center overflow-hidden border-2 border-white/80 ring-2 ring-blue-200/50">
                <img src="@/assets/image/photo_2025-05-26_09-25-06.jpg" alt="Profile" class="w-full h-full object-cover rounded-full transition-transform duration-300 hover:scale-105" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- About Section -->
  <AboutView />
  <!-- Skills Section -->
  <SkillsView />
  <!-- Services Section -->
  <ServicesView />
  <!-- Portfolio Section -->
  <PortfolioView />
  <!-- Contact Section -->
  <ContactView />

 
</template>

<script setup>
import AboutView from '../views/AboutView.vue'
import SkillsView from '../views/SkillsView.vue'
import ServicesView from '../views/ServiceView.vue'
import PortfolioView from '../views/PortfolioView.vue'
import ContactView from '../views/ContactView.vue'

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>