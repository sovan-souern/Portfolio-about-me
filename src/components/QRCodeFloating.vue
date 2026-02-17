<template>
  <div class="fixed bottom-6 right-6 z-50">
    <!-- QR Code Toggle Button -->
    <button 
      @click="toggleQRCode" 
      class="bg-blue-600 hover:bg-blue-700 text-white rounded-full p-4 shadow-lg transition-all duration-300 transform hover:scale-110 group"
      :class="{ 'rotate-90': isOpen }"
    >
      <svg v-if="!isOpen" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v1m6 11h2m-6 0h-2v4m0-11v3m0 0h.01M12 12h4.01M16 20h4M4 12h4m12 0h.01M5 8h2a1 1 0 001-1V5a1 1 0 00-1-1H5a1 1 0 00-1 1v2a1 1 0 001 1zm12 0h2a1 1 0 001-1V5a1 1 0 00-1-1h-2a1 1 0 00-1 1v2a1 1 0 001 1zM5 20h2a1 1 0 001-1v-2a1 1 0 00-1-1H5a1 1 0 00-1 1v2a1 1 0 001 1z" />
      </svg>
      <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
      </svg>
    </button>

    <!-- QR Code Modal -->
    <transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="opacity-0 scale-95 translate-y-2"
      enter-to-class="opacity-100 scale-100 translate-y-0"
      leave-active-class="transition duration-200 ease-in"
      leave-from-class="opacity-100 scale-100 translate-y-0"
      leave-to-class="opacity-0 scale-95 translate-y-2"
    >
      <div v-if="isOpen" class="absolute bottom-16 right-0 bg-white rounded-xl shadow-2xl p-6 w-80 border border-gray-100">
        <div class="text-center">
          <h3 class="text-lg font-semibold text-gray-900 mb-2">Scan to View Portfolio</h3>
          <p class="text-sm text-gray-500 mb-4">Open on your mobile device</p>
          
          <!-- QR Code -->
          <div class="flex justify-center mb-4 bg-gray-50 p-4 rounded-xl">
            <qrcode-vue 
              :value="portfolioUrl" 
              :size="180" 
              level="H" 
              class="bg-white p-2 rounded-lg"
            />
          </div>

          <!-- Current Section -->
          <div class="bg-blue-50 rounded-lg p-3 mb-4">
            <p class="text-xs text-blue-600 mb-1">Current Section:</p>
            <p class="text-sm font-medium text-blue-800 capitalize">{{ currentSection }}</p>
          </div>

          <!-- Action Buttons -->
          <div class="grid grid-cols-2 gap-3">
            <button 
              @click="downloadQRCode" 
              class="bg-green-500 hover:bg-green-600 text-white px-4 py-2.5 rounded-lg text-sm font-medium transition-colors flex items-center justify-center"
            >
              <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4" />
              </svg>
              Download
            </button>
            <button 
              @click="copyUrl" 
              class="bg-blue-500 hover:bg-blue-600 text-white px-4 py-2.5 rounded-lg text-sm font-medium transition-colors flex items-center justify-center"
            >
              <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 16H6a2 2 0 01-2-2V6a2 2 0 012-2h8a2 2 0 012 2v2m-6 12h8a2 2 0 002-2v-8a2 2 0 00-2-2h-8a2 2 0 00-2 2v8a2 2 0 002 2z" />
              </svg>
              {{ copied ? 'Copied!' : 'Copy' }}
            </button>
          </div>

          <!-- Contact Options -->
          <div class="mt-4 pt-4 border-t border-gray-100">
            <p class="text-xs text-gray-500 mb-3">Contact me</p>
            <div class="flex justify-center space-x-4">
              <!-- Telegram -->
              <button @click="openTelegram" class="p-2 bg-blue-100 text-blue-600 rounded-full hover:bg-blue-200 transition-colors group relative">
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm4.64 6.8c-.15 1.58-.8 5.42-1.13 7.19-.14.75-.42 1-.68 1.03-.58.05-1.02-.38-1.58-.75-.88-.58-1.38-.94-2.23-1.5-.99-.65-.35-1.01.22-1.59.15-.15 2.71-2.48 2.76-2.69.01-.03.01-.14-.07-.2-.08-.06-.19-.04-.27-.02-.12.02-1.93 1.23-5.46 3.62-.52.35-1 .52-1.42.51-.47-.01-1.37-.26-2.04-.48-.82-.27-1.47-.42-1.42-.88.03-.24.28-.49.77-.74 2.98-1.29 4.96-2.15 5.94-2.57 2.83-1.21 3.42-1.42 3.8-1.42.08 0 .27.02.39.12.1.08.13.19.14.27-.01.06.01.24 0 .24z"/>
                </svg>
                <span class="absolute -top-8 left-1/2 transform -translate-x-1/2 bg-gray-800 text-white text-xs py-1 px-2 rounded opacity-0 group-hover:opacity-100 transition-opacity whitespace-nowrap">
                  Message me on Telegram
                </span>
              </button>
              
              <!-- WhatsApp Contact - Updated with your WhatsApp link -->
              <button @click="openWhatsApp" class="p-2 bg-green-100 text-green-600 rounded-full hover:bg-green-200 transition-colors group relative">
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.582 2.128 2.182-.573c.978.58 1.911.928 3.145.929 3.178 0 5.767-2.587 5.768-5.766.001-3.187-2.575-5.77-5.764-5.771zm3.392 8.244c-.144.405-.837.774-1.17.824-.299.045-.677.063-1.092-.069-.252-.08-.575-.187-.988-.365-1.739-.751-2.874-2.502-2.961-2.617-.087-.116-.708-.94-.708-1.793s.448-1.273.607-1.446c.159-.173.346-.217.462-.217l.332.006c.106.005.249-.04.39.298.144.347.491 1.2.534 1.287.043.087.072.188.014.304-.058.116-.087.188-.173.289l-.26.304c-.087.087-.177.181-.076.354.101.174.449.741.964 1.201.662.591 1.221.774 1.394.861s.274.072.376-.043c.101-.116.433-.506.549-.68.116-.173.231-.145.39-.087s1.011.477 1.184.564c.173.087.289.13.332.202.043.072.043.419-.101.824z"/>
                </svg>
                <span class="absolute -top-8 left-1/2 transform -translate-x-1/2 bg-gray-800 text-white text-xs py-1 px-2 rounded opacity-0 group-hover:opacity-100 transition-opacity whitespace-nowrap">
                  Contact me on WhatsApp
                </span>
              </button>
              
              <!-- Email - Fixed version -->
              <button @click="openEmailClient" class="p-2 bg-red-100 text-red-600 rounded-full hover:bg-red-200 transition-colors group relative">
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
                </svg>
                <span class="absolute -top-8 left-1/2 transform -translate-x-1/2 bg-gray-800 text-white text-xs py-1 px-2 rounded opacity-0 group-hover:opacity-100 transition-opacity whitespace-nowrap">
                  Send me an email
                </span>
              </button>
            </div>
          </div>

          <!-- Contact Info (Optional - you can remove this if you want) -->
          <div class="mt-3 text-xs text-gray-400">
            <p>SOUERN SOVAN</p>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'
import QrcodeVue from 'qrcode.vue'

const isOpen = ref(false)
const copied = ref(false)
const currentSection = ref('home')

// Your contact information
const telegramUsername = 'Sovansouern'
const yourEmail = 'souernsovan7@gmail.com' // Replace with your actual email
const phoneNumber = '086277461' // Replace with your actual phone number (include country code without +)

// Base portfolio URL
const portfolioUrl = computed(() => {
  const baseUrl = window.location.origin
  return `${baseUrl}/#${currentSection.value}`
})

// Function to detect current section
const updateCurrentSection = () => {
  const sections = ['home', 'about', 'skills', 'services', 'portfolio', 'contact']
  const scrollPosition = window.scrollY + 200

  for (const section of sections) {
    const element = document.getElementById(section)
    if (element) {
      const offsetTop = element.offsetTop
      const offsetHeight = element.offsetHeight
      if (scrollPosition >= offsetTop && scrollPosition < offsetTop + offsetHeight) {
        currentSection.value = section
        break
      }
    }
  }
}

const toggleQRCode = () => {
  isOpen.value = !isOpen.value
  if (isOpen.value) {
    updateCurrentSection()
  }
}

const copyUrl = async () => {
  try {
    await navigator.clipboard.writeText(portfolioUrl.value)
    copied.value = true
    setTimeout(() => {
      copied.value = false
    }, 2000)
  } catch (err) {
    console.error('Failed to copy URL: ', err)
  }
}

const downloadQRCode = () => {
  const canvas = document.querySelector('canvas')
  if (canvas) {
    const link = document.createElement('a')
    link.download = `portfolio-qr-${currentSection.value}.png`
    link.href = canvas.toDataURL('image/png')
    link.click()
  }
}

// Open Telegram direct message
const openTelegram = () => {
  const telegramUrl = `https://t.me/${telegramUsername}`
  window.open(telegramUrl, '_blank')
}

// Open WhatsApp contact - Updated with your WhatsApp link
const openWhatsApp = () => {
  // Format: https://wa.me/phonenumber
  // Make sure phone number includes country code without + or spaces
  const whatsappUrl = `https://wa.me/${phoneNumber}?text=${encodeURIComponent('Hello, I visited your portfolio and would like to connect!')}`
  window.open(whatsappUrl, '_blank')
}

// Fixed Email function
const openEmailClient = () => {
  // Email parameters
  const subject = `Inquiry from Portfolio Visitor - ${currentSection.value} Section`
  
  // Pre-filled message body
  const body = `Hello,

I visited your portfolio and I'm interested in the ${currentSection.value} section.

[Please write your message here]

---
Sent from your portfolio website`
  
  // Create mailto link - Fixed format
  const mailtoLink = `mailto:${yourEmail}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`
  
  // Open default email client
  window.location.href = mailtoLink
  
  // Alternative method if the above doesn't work:
  // window.open(mailtoLink, '_blank')
}

// Handle scroll to update section
const handleScroll = () => {
  if (isOpen.value) {
    updateCurrentSection()
  }
}

// Handle hash changes
const handleHashChange = () => {
  updateCurrentSection()
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  window.addEventListener('hashchange', handleHashChange)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
  window.removeEventListener('hashchange', handleHashChange)
})
</script>