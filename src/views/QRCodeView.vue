<template>
  <div class="min-h-screen bg-gray-50 py-12 px-4 sm:px-6 lg:px-8">
    <div class="max-w-md mx-auto bg-white rounded-xl shadow-md overflow-hidden md:max-w-2xl p-8">
      <div class="text-center">
        <h1 class="text-3xl font-bold text-gray-900 mb-4">Scan to View Portfolio</h1>
        <p class="text-gray-600 mb-8">Scan this QR code with your mobile device to view my portfolio</p>
        
        <!-- QR Code -->
        <div class="flex justify-center mb-8">
          <qrcode-vue 
            :value="portfolioUrl" 
            :size="250" 
            level="H" 
            class="p-4 bg-white border-2 border-gray-200 rounded-lg"
          />
        </div>

        <!-- URL Display -->
        <div class="bg-gray-50 rounded-lg p-4 mb-6">
          <p class="text-sm text-gray-500 mb-2">Portfolio URL:</p>
          <p class="text-blue-600 font-mono text-sm break-all">{{ portfolioUrl }}</p>
        </div>

        <!-- Download Button -->
        <button 
          @click="downloadQRCode" 
          class="w-full bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-6 rounded-lg transition-colors flex items-center justify-center"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4" />
          </svg>
          Download QR Code
        </button>

        <!-- Share Options -->
        <div class="mt-8">
          <p class="text-gray-600 mb-4">Or share via:</p>
          <div class="flex justify-center space-x-4">
            <button @click="shareVia('email')" class="p-3 bg-red-100 text-red-600 rounded-full hover:bg-red-200 transition-colors">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
              </svg>
            </button>
            <button @click="shareVia('whatsapp')" class="p-3 bg-green-100 text-green-600 rounded-full hover:bg-green-200 transition-colors">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z" />
              </svg>
            </button>
            <button @click="shareVia('twitter')" class="p-3 bg-blue-100 text-blue-600 rounded-full hover:bg-blue-200 transition-colors">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 8h10M7 12h4m1 8l-4-4H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-3l-4 4z" />
              </svg>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import QrcodeVue from 'qrcode.vue'

export default {
  name: 'QRCodePage',
  components: {
    QrcodeVue
  },
  data() {
    return {
      portfolioUrl: window.location.origin + '/portfolio-about-me'
    }
  },
  methods: {
    downloadQRCode() {
      const canvas = document.querySelector('canvas')
      if (canvas) {
        const link = document.createElement('a')
        link.download = 'my-portfolio-qr.png'
        link.href = canvas.toDataURL('image/png')
        link.click()
      }
    },
    shareVia(platform) {
      const text = 'Check out my portfolio!'
      const url = this.portfolioUrl
      
      let shareUrl = ''
      switch(platform) {
        case 'email':
          shareUrl = `mailto:?subject=${encodeURIComponent(text)}&body=${encodeURIComponent(url)}`
          break
        case 'whatsapp':
          shareUrl = `https://wa.me/?text=${encodeURIComponent(text + ' ' + url)}`
          break
        case 'twitter':
          shareUrl = `https://twitter.com/intent/tweet?text=${encodeURIComponent(text)}&url=${encodeURIComponent(url)}`
          break
      }
      
      if (shareUrl) {
        window.open(shareUrl, '_blank')
      }
    }
  }
}
</script>