<template>
  <section id="services" class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16">
        <span class="inline-block px-4 py-2 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mb-4">
          Services
        </span>
        <h2 class="text-4xl md:text-5xl font-bold mb-6 text-gray-900">
          What I Offer
        </h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          Comprehensive development services to bring your ideas to life
        </p>
      </div>

      <!-- Services Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 mb-20">
        <div v-for="service in services" :key="service.id" class="group">
          <div class="bg-white border border-gray-200 rounded-xl p-8 hover:border-blue-300 transition-all duration-300 hover:shadow-lg h-full">
            <h3 class="text-2xl font-semibold text-gray-900 mb-4">{{ service.title }}</h3>
            <p class="text-gray-600 mb-6 leading-relaxed">{{ service.description }}</p>
            <ul class="space-y-3 mb-8">
              <li v-for="feature in service.features" :key="feature" class="flex items-center text-gray-600">
                <span class="text-green-500 mr-3">✓</span>
                {{ feature }}
              </li>
            </ul>
            <div class="text-2xl font-bold text-blue-600 mb-6">
              {{ service.price }}
            </div>
            <button @click="scrollToSection('contact')" class="w-full bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700 transition-all duration-300 shadow-lg">
              Get Started
            </button>
          </div>
        </div>
      </div>

      <!-- Process Section -->
      <div class="bg-gray-50 border border-gray-200 rounded-2xl p-12 shadow-lg">
        <h3 class="text-3xl font-bold text-center mb-12 text-gray-900">My Process</h3>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div v-for="(step, index) in process" :key="step.id" class="text-center group">
            <div class="bg-blue-600 text-white rounded-full w-16 h-16 flex items-center justify-center text-2xl font-bold mx-auto mb-6 group-hover:scale-110 transition-transform duration-300 shadow-lg">
              {{ index + 1 }}
            </div>
            <h4 class="text-xl font-semibold text-gray-900 mb-3">{{ step.title }}</h4>
            <p class="text-gray-600 leading-relaxed">{{ step.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const services = [
  {
    id: 1,
    title: 'Web Development',
    description: 'Custom web applications built with modern technologies and best practices for optimal performance and user experience.',
    features: ['Responsive Design', 'Performance Optimization', 'SEO Friendly', 'Cross-browser Compatible', 'Modern Frameworks'],
    price: 'Negotiable'
  },
  {
    id: 2,
    title: 'POS System Development',
    description: 'Custom Point of Sale (POS) systems tailored to your business needs, with features like inventory management, sales tracking, and customer management.',
    features: ['Inventory Management', 'Sales Tracking', 'Customer Management', 'Reporting & Analytics', 'Multi-platform Support'],
    price: 'Negotiable'
  },
  {
    id: 3,
    title: 'E-Commerce Solutions',
    description: 'Complete online store development with payment integration, inventory management, and analytics.',
    features: ['Payment Integration', 'Inventory Management', 'Admin Dashboard', 'Analytics', 'Security'],
    price: 'Negotiable'
  },
  {
    id: 4,
    title: 'UI/UX Design',
    description: 'User-centered design for web and mobile applications that prioritize usability and aesthetics.',
    features: ['User Research', 'Wireframing', 'Prototyping', 'Design Systems', 'Usability Testing'],
    price: 'Negotiable'
  },
  {
    id: 5,
    title: 'API Development',
    description: 'RESTful APIs and backend services with robust architecture, security, and documentation.',
    features: ['Database Design', 'Authentication', 'Documentation', 'Testing', 'Scalability'],
    price: 'Negotiable'
  },
  {
    id: 6,
    title: 'Quality Assurance',
    description: 'Technical consulting and code review services to improve your development processes and code quality.',
    features: ['Write Test Cases', 'Manual Testing', 'Performance Testing', 'Security Testing', 'Code Review','API Testing'],
    price: 'Negotiable'
  }
]

const process = [
  {
    id: 1,
    title: 'Discovery',
    description: 'Understanding your requirements, goals, target audience, and project scope through detailed discussions.'
  },
  {
    id: 2,
    title: 'Planning',
    description: 'Creating detailed project roadmap, timeline, technical specifications, and design mockups.'
  },
  {
    id: 3,
    title: 'Development',
    description: 'Building your solution with regular updates, feedback sessions, and iterative improvements.'
  },
  {
    id: 4,
    title: 'Delivery',
    description: 'Testing, deployment, training, documentation, and ongoing support for your project.'
  }
]

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>