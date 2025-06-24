<template>
  <section id="portfolio" class="py-20 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16">
        <span class="inline-block px-4 py-2 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mb-4">
          Portfolio
        </span>
        <h2 class="text-4xl md:text-5xl font-bold mb-6 text-gray-900">
          Featured Projects
        </h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          A showcase of my best work and creative solutions
        </p>
      </div>

      <!-- Filter Buttons -->
      <div class="flex flex-wrap justify-center gap-4 mb-12">
        <button v-for="category in portfolioCategories" :key="category" @click="selectedCategory = category" :class="[
          'px-6 py-3 rounded-lg font-medium transition-all duration-300',
          selectedCategory === category
            ? 'bg-blue-600 text-white shadow-lg'
            : 'bg-white text-gray-600 hover:bg-blue-50 hover:text-blue-600 border border-gray-200'
        ]">
          {{ category }}
        </button>
      </div>

      <!-- Portfolio Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div v-for="project in filteredProjects" :key="project.id" class="group">
          <div class="bg-white border border-gray-200 rounded-xl overflow-hidden hover:border-blue-300 transition-all duration-300 hover:shadow-lg transform hover:-translate-y-2">
            <div class="relative overflow-hidden">
              <!-- Project Image -->
              <div class="w-full h-48 relative">
                <img 
                  :src="project.image" 
                  :alt="project.title"
                  class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-300"
                  @error="handleImageError"
                />
                <!-- Fallback for broken images -->
                <div v-if="project.imageError" class="absolute inset-0 bg-gradient-to-br from-blue-50 to-blue-100 flex items-center justify-center">
                  <div class="text-center">
                    <div class="w-16 h-16 bg-blue-600 rounded-lg flex items-center justify-center mx-auto mb-2">
                      <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"></path>
                      </svg>
                    </div>
                    <p class="text-blue-600 text-sm font-medium">{{ project.title }}</p>
                  </div>
                </div>
              </div>
              <!-- Hover Overlay -->
              <div class="absolute inset-0 bg-black/50 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
                <div class="flex space-x-4">
                  <button @click="viewProject(project)" class="bg-white text-gray-900 px-4 py-2 rounded-lg hover:bg-gray-100 transition-colors duration-200 font-medium">
                    View
                  </button>
                  <button @click="openLiveDemo(project)" class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition-all duration-200 font-medium">
                    Live
                  </button>
                </div>
              </div>
            </div>
            <div class="p-6">
              <div class="flex items-center justify-between mb-3">
                <h3 class="text-xl font-semibold text-gray-900">{{ project.title }}</h3>
                <span class="px-3 py-1 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium">
                  {{ project.category }}
                </span>
              </div>
              <p class="text-gray-600 mb-4">{{ project.description }}</p>
              <div class="flex flex-wrap gap-2">
                <span v-for="tech in project.technologies" :key="tech" class="px-2 py-1 bg-gray-100 text-gray-600 text-xs rounded-full hover:bg-blue-50 hover:text-blue-600 transition-colors duration-200">
                  {{ tech }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Empty State -->
      <div v-if="filteredProjects.length === 0" class="text-center py-16">
        <div class="w-16 h-16 bg-gray-100 rounded-full flex items-center justify-center mx-auto mb-4">
          <svg class="w-8 h-8 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"></path>
          </svg>
        </div>
        <h3 class="text-lg font-semibold text-gray-900 mb-2">No projects found</h3>
        <p class="text-gray-500">Try selecting a different category</p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const portfolioCategories = ['All', 'Web', 'Mobile', 'Design', 'API']
const selectedCategory = ref('All')

const projects = ref([
  {
    id: 1,
    title: 'Sport Website',
    category: 'Web',
    description: 'A dynamic website showcasing sports events and scores with interactive features.',
    technologies: ['Vue.js', 'Tailwind CSS', 'JavaScript'],
    image: './src/assets/image/sport.jpg',
    liveUrl: 'http://sport-club-b8.netlify.app',
    githubUrl: 'https://github.com/sovan-souern/sport',
    imageError: false
  },
  {
    id: 2,
    title: 'System Management Tool',
    category: 'Web',
    description: 'An online store with payment integration and admin dashboard.',
    technologies: ['Python','Tkinter'],
    image: './src/assets/image/system.jpg',
    liveUrl: '#',
    githubUrl: '',
    imageError: false
  },
  {
    id: 3,
    title: 'Weather App',
    category: 'Mobile',
    description: 'A real-time chat application for iOS and Android.',
    technologies: ['Javascript', 'HTML','CSS', 'Firebase'],
    image: './src/assets/image/weather.jpg',
    liveUrl: 'https://weather-app-g16.netlify.app/page/home.html',
    githubUrl: 'https://github.com/sovan-souern/Weather-App-G16',
    imageError: false
  },
  {
    id: 4,
    title: 'Brand Identity Design',
    category: 'Design',
    description: 'Complete brand identity package including logo, colors, and guidelines.',
    technologies: ['Figma', 'Adobe Illustrator', 'Photoshop'],
    image: 'https://img.freepik.com/free-vector/business-hand-drawn-e-commerce-landing-page_23-2149600513.jpg?semt=ais_hybrid&w=740',
    liveUrl: '#',
    githubUrl: 'https://github.com/sovan-souern/VC1-G10',
    imageError: false
  },
  {
    id: 5,
    title: 'Deploying Website (AWS)',
    category: 'API',
    description: 'A scalable RESTful API for a content management system.',
    technologies: ['AWS(EC2)', 'Docker', 'Node.js'],
    image: 'https://i.pinimg.com/736x/09/3f/6e/093f6ed3ff0b96f50686bd538383ad9c.jpg',
    liveUrl: '#',
    githubUrl: '#',
    imageError: false
  },
  {
    id: 6,
    title: 'Personal(Code Learning)',
    category: 'Web',
    description: 'A personal project focused on learning coding concepts and best practices.',
    technologies: ['HTML', 'CSS', 'Javascript', 'Bootstrap5'],
    image: './src/assets/image/code.jpg',
    liveUrl: 'https://sovan-souern.github.io/codelearning/',
    githubUrl: 'https://github.com/sovan-souern/codelearning',
    imageError: false
  }
])

const filteredProjects = computed(() => {
  if (selectedCategory.value === 'All') {
    return projects.value
  }
  return projects.value.filter(project => project.category === selectedCategory.value)
})

const handleImageError = (event) => {
  const img = event.target
  const projectId = parseInt(img.closest('[data-project-id]')?.dataset.projectId)
  if (projectId) {
    const project = projects.value.find(p => p.id === projectId)
    if (project) {
      project.imageError = true
    }
  }
}

const viewProject = (project) => {
  if (project.githubUrl && project.githubUrl !== '#') {
    window.open(project.githubUrl, '_blank')
  } else {
    console.log('View project:', project.title)
    // Add your view project logic here
  }
}

const openLiveDemo = (project) => {
  if (project.liveUrl && project.liveUrl !== '#') {
    window.open(project.liveUrl, '_blank')
  } else {
    console.log('Open live demo:', project.title)
    // Add your live demo logic here
  }
}

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>