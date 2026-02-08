<template>
  <section id="contact" class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16">
        <span class="inline-block px-4 py-2 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mb-4">
          Contact
        </span>
        <h2 class="text-4xl md:text-5xl font-bold mb-6 text-gray-900">
          Get in Touch
        </h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          I'd love to hear from you! Reach out for collaborations or inquiries.
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
        <!-- Contact Information Card -->
        <div class="bg-white border border-gray-100 rounded-2xl p-8 shadow-sm hover:shadow-md transition-shadow duration-300">
          <div class="space-y-8">
            <div>
              <h3 class="text-2xl font-semibold text-gray-900 mb-8">Contact Details</h3>
              <div class="space-y-6">
                <div class="flex items-center group">
                  <div class="w-6 h-6 rounded-full bg-blue-100 flex items-center justify-center mr-4 group-hover:bg-blue-200 transition-colors duration-200">
                    <svg class="w-4 h-4 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
                    </svg>
                  </div>
                  <a 
                    href="mailto:souernsovan7@gmail.com" 
                    class="text-gray-700 hover:text-blue-600 transition-colors duration-200 text-lg"
                  >
                    souernsovan7@gmail.com
                  </a>
                </div>
                
                <div class="flex items-center group">
                  <div class="w-6 h-6 rounded-full bg-pink-100 flex items-center justify-center mr-4 group-hover:bg-pink-200 transition-colors duration-200">
                    <svg class="w-4 h-4 text-pink-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/>
                    </svg>
                  </div>
                  <span class="text-gray-700 text-lg">+855 86277461</span>
                </div>
                
                <div class="flex items-center group">
                  <div class="w-6 h-6 rounded-full bg-red-100 flex items-center justify-center mr-4 group-hover:bg-red-200 transition-colors duration-200">
                    <svg class="w-4 h-4 text-red-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/>
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/>
                    </svg>
                  </div>
                  <span class="text-gray-700 text-lg">Phnom Penh, Cambodia</span>
                </div>
              </div>
            </div>

            <!-- Social Links -->
            <div>
              <h4 class="text-xl font-semibold text-gray-900 mb-6">Follow Me</h4>
              <div class="flex space-x-8">
                <a href="#" class="text-gray-500 hover:text-gray-700 flex items-center space-x-2 group">
                  <svg class="w-5 h-5 group-hover:scale-110 transition-transform" fill="currentColor" viewBox="0 0 24 24">
                    <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                  </svg>
                  <span>GitHub</span>
                </a>
              </div>
            </div>
          </div>
        </div>

        <!-- Contact Form -->
        <div class="bg-white border border-gray-100 rounded-2xl p-8 shadow-sm hover:shadow-md transition-shadow duration-300">
          <h3 class="text-2xl font-semibold text-gray-900 mb-8">Send Me a Message</h3>
          <form @submit.prevent="handleSubmit" class="space-y-6">
            
            <div class="space-y-2">
              <label for="name" class="block text-sm font-medium text-gray-700">Name</label>
              <input v-model="form.name" type="text" id="name"
                class="w-full px-4 py-3 border border-gray-200 rounded-xl bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:bg-white"
                placeholder="Your Name" required>
            </div>

            <div class="space-y-2">
              <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
              <input v-model="form.email" type="email" id="email"
                class="w-full px-4 py-3 border border-gray-200 rounded-xl bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:bg-white"
                placeholder="your@email.com" required>
            </div>

            <div class="space-y-2">
              <label for="message" class="block text-sm font-medium text-gray-700">Message</label>
              <textarea v-model="form.message" id="message" rows="5"
                class="w-full px-4 py-3 border border-gray-200 rounded-xl bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:bg-white resize-none"
                placeholder="Your Message" required></textarea>
            </div>

            <button type="submit" :disabled="isSubmitting"
              class="w-full bg-blue-600 text-white px-6 py-3 rounded-xl hover:bg-blue-700 focus:ring-4 focus:ring-blue-200 disabled:opacity-50 flex items-center justify-center space-x-2">

              <svg v-if="!isSubmitting" class="w-4 h-4" fill="none" stroke="currentColor"
                viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                  d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8" />
              </svg>

              <svg v-else class="w-4 h-4 animate-spin" fill="none" viewBox="0 0 24 24">
                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor"
                  stroke-width="4"></circle>
                <path class="opacity-75" fill="currentColor"
                  d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
              </svg>

              <span>{{ isSubmitting ? 'Sending...' : 'Send Message' }}</span>
            </button>
          </form>

          <div v-if="submissionMessage"
            class="mt-6 p-4 bg-green-50 border border-green-200 rounded-xl flex items-center space-x-3">
            <svg class="w-5 h-5 text-green-600" fill="none" stroke="currentColor"
              viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
            <p class="text-green-700 text-sm">{{ submissionMessage }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import emailjs from 'emailjs-com'

const form = ref({
  name: '',
  email: '',
  message: ''
})

const submissionMessage = ref('')
const isSubmitting = ref(false)

const handleSubmit = async () => {
  isSubmitting.value = true

  const templateParams = {
    from_name: form.value.name,
    from_email: form.value.email,
    message: form.value.message
  }

  try {
    await emailjs.send(
      'YOUR_SERVICE_ID',      // <-- replace
      'YOUR_TEMPLATE_ID',     // <-- replace
      templateParams,
      'YOUR_PUBLIC_KEY'       // <-- replace
    )

    submissionMessage.value = "Message sent successfully! I'll get back to you soon."
    form.value = { name: '', email: '', message: '' }

    setTimeout(() => submissionMessage.value = '', 5000)

  } catch (error) {
    submissionMessage.value = 'Failed to send message.'
    console.error('EmailJS Error:', error)
  }

  isSubmitting.value = false
}
</script>

<style scoped>
input:focus,
textarea:focus {
  outline: none;
}

* {
  transition-property: color, background-color, border-color, transform, box-shadow;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

.animate-spin {
  animation: spin 1s linear infinite;
}
</style>
