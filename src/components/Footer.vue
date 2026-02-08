<template>
  <footer class="bg-white border-t border-gray-200 py-12">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
        <div class="col-span-1 md:col-span-2">
          <div class="flex items-center mb-4">
            <div class="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center mr-3">
              <span class="text-white font-bold text-lg">JD</span>
            </div>
            <span class="text-xl font-bold text-gray-900">Sovan Souern</span>
          </div>
          <p class="text-gray-600 mb-6 leading-relaxed max-w-md">
            WEB Developer passionate about creating amazing digital experiences that make a difference in the world.
          </p>
          <div class="flex space-x-4">
            <a href="#" class="text-gray-400 hover:text-blue-600 transition-colors duration-200">GitHub</a>
            <a href="#" class="text-gray-400 hover:text-blue-600 transition-colors duration-200">LinkedIn</a>
            <a href="#" class="text-gray-400 hover:text-blue-600 transition-colors duration-200">Twitter</a>
            <a href="#" class="text-gray-400 hover:text-blue-600 transition-colors duration-200">Email</a>
          </div>
        </div>
        <div>
          <h4 class="text-lg font-semibold text-gray-900 mb-4">Quick Links</h4>
          <ul class="space-y-2">
            <li><button @click="scrollToSection('home')" class="text-gray-600 hover:text-blue-600 transition-colors duration-200">Home</button></li>
            <li><button @click="scrollToSection('about')" class="text-gray-600 hover:text-blue-600 transition-colors duration-200">About</button></li>
            <li><button @click="scrollToSection('skills')" class="text-gray-600 hover:text-blue-600 transition-colors duration-200">Skills</button></li>
            <li><button @click="scrollToSection('services')" class="text-gray-600 hover:text-blue-600 transition-colors duration-200">Services</button></li>
            <li><button @click="scrollToSection('portfolio')" class="text-gray-600 hover:text-blue-600 transition-colors duration-200">Portfolio</button></li>
            <li><button @click="scrollToSection('contact')" class="text-gray-600 hover:text-blue-600 transition-colors duration-200">Contact</button></li>
          </ul>
        </div>
        <div>
          <h4 class="text-lg font-semibold text-gray-900 mb-4">Contact</h4>
          <ul class="space-y-2 text-gray-600">
            <li>souernsovan7@gmail.com</li>
            <li>+855 86277461</li>
            <li>Phnom Penh, Cambodia</li>
          </ul>
        </div>
      </div>
      <div class="border-t border-gray-200 mt-8 pt-8 text-center text-gray-600">
        <p>© 2025 Sovan Souern. All rights reserved. Made with Vue.js</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>