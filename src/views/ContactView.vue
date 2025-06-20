<template>
  <div class="contact-view py-20">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-20">
        <h1 class="text-5xl md:text-6xl font-bold mb-6">Get In Touch</h1>
        <div class="w-24 h-1 bg-gradient-to-r from-blue-400 to-purple-600 mx-auto mb-8"></div>
        <p class="text-xl text-gray-400 max-w-3xl mx-auto">
          Ready to start your next project? Let's discuss how we can work together.
        </p>
      </div>

      <div class="grid lg:grid-cols-2 gap-16">
        <div>
          <h2 class="text-3xl font-bold mb-8">Contact Information</h2>
          <div class="space-y-6">
            <div class="flex items-center">
              <div class="w-14 h-14 bg-gradient-to-r from-blue-500 to-purple-600 rounded-lg flex items-center justify-center mr-4">
                <span class="text-white text-xl">📧</span>
              </div>
              <div>
                <h3 class="text-lg font-semibold text-blue-400">Email</h3>
                <p class="text-gray-300">contact@portfolio.com</p>
              </div>
            </div>
            
            <div class="flex items-center">
              <div class="w-14 h-14 bg-gradient-to-r from-blue-500 to-purple-600 rounded-lg flex items-center justify-center mr-4">
                <span class="text-white text-xl">📱</span>
              </div>
              <div>
                <h3 class="text-lg font-semibold text-blue-400">Phone</h3>
                <p class="text-gray-300">+1 (555) 123-4567</p>
              </div>
            </div>
          </div>
        </div>

        <div class="bg-gray-900 p-8 rounded-2xl">
          <h2 class="text-2xl font-bold mb-6">Send Message</h2>
          <form @submit.prevent="submitForm" class="space-y-6">
            <div>
              <input 
                type="text" 
                v-model="form.name"
                placeholder="Your Name"
                class="w-full px-4 py-3 bg-gray-800 border border-gray-700 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-white placeholder-gray-400"
                required
              >
            </div>
            <div>
              <input 
                type="email" 
                v-model="form.email"
                placeholder="Your Email"
                class="w-full px-4 py-3 bg-gray-800 border border-gray-700 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-white placeholder-gray-400"
                required
              >
            </div>
            <div>
              <textarea 
                v-model="form.message"
                rows="5"
                placeholder="Your Message"
                class="w-full px-4 py-3 bg-gray-800 border border-gray-700 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-white placeholder-gray-400"
                required
              ></textarea>
            </div>
            <button 
              type="submit"
              class="w-full bg-gradient-to-r from-blue-600 to-purple-600 text-white py-4 px-6 rounded-lg hover:from-blue-700 hover:to-purple-700 transition-all duration-300 font-semibold"
            >
              Send Message
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from 'vue'

const form = reactive({
  name: '',
  email: '',
  message: ''
})

const submitForm = () => {
  alert('Message sent successfully!')
  form.name = ''
  form.email = ''
  form.message = ''
}
</script>