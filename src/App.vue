<template>
  <div id="app" class="bg-white text-gray-900 min-h-screen">
    <!-- Navigation -->
    <nav class="fixed w-full top-0 z-50 bg-white/95 backdrop-blur-md border-b border-gray-200 shadow-sm">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between items-center py-4">
          <!-- Logo -->
          <div class="flex items-center">
            <div class="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center mr-3">
              <span class="text-white font-bold text-lg">SV</span>
            </div>
            <span class="text-xl font-bold text-gray-900">
              Sovan Souern
            </span>
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

    <!-- Main Content -->
    <main class="pt-20">
      <!-- Home Section -->
      <section id="home" class="min-h-screen flex items-center relative overflow-hidden bg-gray-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full relative z-10">
          <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
            <div class="text-center lg:text-left">
              <div class="mb-6">
                <span
                  class="inline-block px-4 py-2 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mb-4">
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
                <button @click="scrollToSection('skills')"
                  class="bg-blue-600 text-white px-8 py-4 rounded-lg font-semibold text-lg hover:bg-blue-700 transition-all duration-300 transform hover:scale-105 shadow-lg">
                  View My Skills
                </button>
                <button @click="scrollToSection('contact')"
                  class="border-2 border-blue-600 text-blue-600 px-8 py-4 rounded-lg font-semibold text-lg hover:bg-blue-600 hover:text-white transition-all duration-300">
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
                <!-- Profile Image -->
                <div
                  class="w-80 h-80 rounded-full bg-gradient-to-br from-blue-100 to-blue-300 via-blue-200 border-4 border-blue-600 shadow-xl hover:shadow-2xl transition-shadow duration-300 flex items-center justify-center transform hover:-translate-y-2 hover:rotate-1">
                  <div
                    class="w-72 h-72 rounded-full bg-white flex items-center justify-center overflow-hidden border-2 border-white/80 ring-2 ring-blue-200/50">
                    <img src="@/assets/image/photo_2025-05-26_09-25-06.jpg" alt="Profile"
                      class="w-full h-full object-cover rounded-full transition-transform duration-300 hover:scale-105" />
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- About Section -->
      <section id="about" class="py-20 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="text-center mb-16">
            <span
              class="inline-block px-4 py-2 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mb-4">
              About Me
            </span>
            <h2 class="text-4xl md:text-5xl font-bold mb-6 text-gray-900">
              My Journey & Expertise
            </h2>
            <p class="text-xl text-gray-600 max-w-3xl mx-auto">
              Passionate about creating digital solutions that make a real impact
            </p>
          </div>

          <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center mb-20">
            <div>
              <!-- About Image -->
              <div
                class="relative flex items-center justify-center w-full h-96 rounded-2xl bg-white shadow-lg hover:shadow-xl transition-shadow duration-300 overflow-hidden">
                <img src="@/assets/image/photo_2025-05-26_09-25-06.jpg" alt="About Me Full Image"
                  class="object-contain w-full h-full transition-transform duration-300 hover:scale-105" />
              </div>
            </div>
            <div>
              <h3 class="text-3xl font-bold mb-6 text-gray-900">My Story</h3>
              <div class="space-y-6 text-gray-600 leading-relaxed">
                <p>
                  I'm a student passionate about web development, exploring this field through school projects. My
                  journey began with curiosity about how websites are built, sparking my interest in coding and design.
                </p>
                <p>
                  I’m learning modern web technologies like React, Vue.js, HTML, and CSS through my coursework. I enjoy
                  creating projects that are functional and aim to improve my skills with each assignment.
                </p>
                <p>
                  Outside of school, I love experimenting with new tools, working on personal coding projects, and
                  learning from online resources to grow my knowledge.
                </p>
              </div>
              <button @click="scrollToSection('contact')"
                class="mt-8 bg-blue-600 text-white px-8 py-3 rounded-lg font-semibold hover:bg-blue-700 transition-all duration-300 shadow-lg">
                Let's Work Together
              </button>
            </div>
          </div>

          <!-- Experience Timeline -->
          <div>
            <h3 class="text-3xl font-bold text-center mb-12 text-gray-900">Professional Experience</h3>
            <div class="space-y-8">
              <div v-for="exp in experience" :key="exp.id" class="group">
                <div
                  class="bg-white border border-gray-200 rounded-xl p-8 hover:border-blue-300 transition-all duration-300 hover:shadow-lg">
                  <div class="flex flex-col md:flex-row md:items-center md:justify-between mb-4">
                    <div>
                      <h4 class="text-xl font-semibold text-gray-900 mb-1">{{ exp.position }}</h4>
                      <p class="text-blue-600 font-medium">{{ exp.company }}</p>
                    </div>
                    <span
                      class="inline-block px-3 py-1 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mt-2 md:mt-0">
                      {{ exp.period }}
                    </span>
                  </div>
                  <p class="text-gray-600 mb-4 leading-relaxed">{{ exp.description }}</p>
                  <div class="flex flex-wrap gap-2">
                    <span v-for="tech in exp.technologies" :key="tech"
                      class="px-3 py-1 bg-gray-100 text-gray-700 text-sm rounded-full hover:bg-blue-50 hover:text-blue-600 transition-colors duration-200">
                      {{ tech }}
                    </span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Enhanced Skills & Tools Section -->
      <section id="skills" class="py-20 bg-gray-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="text-center mb-16">
            <span
              class="inline-block px-4 py-2 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mb-4">
              Skills & Tools
            </span>
            <h2 class="text-4xl md:text-5xl font-bold mb-6 text-gray-900">
              My Technical Arsenal
            </h2>
            <p class="text-xl text-gray-600 max-w-3xl mx-auto">
              Interactive showcase of my technical skills and the tools I use for development and learning
            </p>
          </div>

          <!-- Category Toggle -->
          <div class="flex justify-center mb-12">
            <div class="bg-white border border-gray-200 rounded-lg p-2 shadow-lg">
              <button @click="activeTab = 'skills'" :class="[
                'px-6 py-3 rounded-lg font-medium transition-all duration-300',
                activeTab === 'skills'
                  ? 'bg-blue-600 text-white shadow-lg'
                  : 'text-gray-600 hover:text-blue-600'
              ]">
                💻 Technical Skills
              </button>
              <button @click="activeTab = 'tools'" :class="[
                'px-6 py-3 rounded-lg font-medium transition-all duration-300',
                activeTab === 'tools'
                  ? 'bg-blue-600 text-white shadow-lg'
                  : 'text-gray-600 hover:text-blue-600'
              ]">
                🛠️ Tools & Resources
              </button>
            </div>
          </div>

          <!-- Skills Tab -->
          <div v-show="activeTab === 'skills'" class="space-y-12">
            <!-- Skill Categories -->
            <div class="flex flex-wrap justify-center gap-4 mb-8">
              <button v-for="category in skillCategories" :key="category" @click="selectedSkillCategory = category"
                :class="[
                  'px-6 py-3 rounded-lg font-medium transition-all duration-300',
                  selectedSkillCategory === category
                    ? 'bg-blue-600 text-white shadow-lg'
                    : 'bg-white text-gray-600 hover:bg-blue-50 hover:text-blue-600 border border-gray-200'
                ]">
                {{ category }}
              </button>
            </div>

            <!-- Skills Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
              <div v-for="skill in filteredSkills" :key="skill.name" class="group cursor-pointer"
                @click="selectSkill(skill)">
                <div
                  class="bg-white border border-gray-200 rounded-xl p-6 hover:border-blue-300 transition-all duration-300 hover:shadow-lg transform hover:-translate-y-2 h-full">
                  <div class="flex items-center mb-4">
                    <div
                      class="w-12 h-12 bg-white border border-gray-200 rounded-lg flex items-center justify-center mr-4 p-1 skill-icon-container">
                      <img v-if="skill.image" :src="skill.image" :alt="`Logo for ${skill.name}`"
                        class="w-full h-full object-contain skill-image" @error="skill.image = null">
                      <span v-else class="text-blue-600 font-bold text-sm">{{ skill.icon }}</span>
                    </div>
                    <div class="flex-1">
                      <h4 class="text-lg font-semibold text-gray-900">{{ skill.name }}</h4>
                      <p class="text-sm text-gray-500">{{ skill.category }}</p>
                    </div>
                  </div>
                  <p class="text-gray-600 text-sm mb-4">{{ skill.description }}</p>
                  <!-- Experience Badge -->
                  <div class="mb-4">
                    <span
                      class="inline-block px-3 py-1 bg-blue-50 text-blue-600 text-xs rounded-full font-medium border border-blue-200">
                      {{ skill.experience }}
                    </span>
                  </div>
                  <!-- Tools Used -->
                  <div class="flex flex-wrap gap-2">
                    <span v-for="tool in skill.tools?.slice(0, 2)" :key="tool"
                      class="px-2 py-1 bg-gray-100 text-gray-600 text-xs rounded-full hover:bg-blue-50 hover:text-blue-600 transition-colors duration-200">
                      {{ tool }}
                    </span>
                    <span v-if="skill.tools?.length > 2"
                      class="px-2 py-1 bg-gray-100 text-gray-600 text-xs rounded-full">
                      +{{ skill.tools.length - 2 }}
                    </span>
                  </div>
                </div>
              </div>
            </div>

            <!-- Selected Skill Detail -->
            <div v-if="selectedSkill" class="bg-white border border-gray-200 rounded-2xl p-8 shadow-lg">
              <div class="text-center mb-6">
                <div
                  class="w-20 h-20 bg-white border border-gray-200 rounded-xl flex items-center justify-center mx-auto mb-4 p-2 skill-icon-container">
                  <img v-if="selectedSkill.image" :src="selectedSkill.image" :alt="`Logo for ${selectedSkill.name}`"
                    class="w-full h-full object-contain skill-image" @error="selectedSkill.image = null">
                  <span v-else class="text-blue-600 font-bold text-2xl">{{ selectedSkill.icon }}</span>
                </div>
                <h3 class="text-2xl font-bold text-gray-900 mb-2">{{ selectedSkill.name }}</h3>
                <p class="text-blue-600 font-medium">{{ selectedSkill.category }} • {{ selectedSkill.experience }}</p>
              </div>
              <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div>
                  <h4 class="text-lg font-semibold text-gray-900 mb-4">About This Skill</h4>
                  <p class="text-gray-600 leading-relaxed mb-6">{{ selectedSkill.description }}</p>
                  <h4 class="text-lg font-semibold text-gray-900 mb-4">Tools I Use</h4>
                  <div class="flex flex-wrap gap-2">
                    <span v-for="tool in selectedSkill.tools" :key="tool"
                      class="px-3 py-1 bg-blue-50 text-blue-600 text-sm rounded-full border border-blue-200">
                      {{ tool }}
                    </span>
                  </div>
                </div>
                <div>
                  <h4 class="text-lg font-semibold text-gray-900 mb-4">Projects Built</h4>
                  <ul class="space-y-2">
                    <li v-for="project in selectedSkill.projects" :key="project"
                      class="flex items-center text-gray-600">
                      <span class="text-green-500 mr-2">✓</span>
                      {{ project }}
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <!-- Tools Tab -->
          <div v-show="activeTab === 'tools'" class="space-y-12">
            <!-- Tool Categories -->
            <div class="flex flex-wrap justify-center gap-4 mb-8">
              <button v-for="category in toolCategories" :key="category" @click="selectedToolCategory = category"
                :class="[
                  'px-6 py-3 rounded-lg font-medium transition-all duration-300',
                  selectedToolCategory === category
                    ? 'bg-blue-600 text-white shadow-lg'
                    : 'bg-white text-gray-600 hover:bg-blue-50 hover:text-blue-600 border border-gray-200'
                ]">
                {{ category }}
              </button>
            </div>

            <!-- Tools Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
              <div v-for="tool in filteredTools" :key="tool.name" class="group cursor-pointer"
                @click="selectTool(tool)">
                <div
                  class="bg-white border border-gray-200 rounded-xl p-6 hover:border-blue-300 transition-all duration-300 hover:shadow-lg transform hover:-translate-y-2 h-full">
                  <div class="flex items-center mb-4">
                    <div
                      class="w-16 h-16 bg-gradient-to-br from-blue-500 to-indigo-600 rounded-xl flex items-center justify-center mr-4">
                      <span class="text-white text-xl font-bold">{{ tool.icon }}</span>
                    </div>
                    <div>
                      <h4 class="text-lg font-semibold text-gray-900">{{ tool.name }}</h4>
                      <p class="text-sm text-blue-600">{{ tool.category }}</p>
                    </div>
                  </div>
                  <p class="text-gray-600 text-sm mb-4">{{ tool.description }}</p>
                  <!-- Usage Level -->
                  <div class="flex items-center justify-between mb-4">
                    <span class="text-sm text-gray-500">Usage Level</span>
                    <span class="text-sm font-medium text-blue-600">{{ tool.usage }}</span>
                  </div>
                  <!-- Features -->
                  <div class="space-y-2">
                    <div v-for="feature in tool.features.slice(0, 2)" :key="feature"
                      class="flex items-center text-sm text-gray-600">
                      <span class="text-green-500 mr-2">•</span>
                      {{ feature }}
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <!-- Selected Tool Detail -->
            <div v-if="selectedTool" class="bg-white border border-gray-200 rounded-2xl p-8 shadow-lg">
              <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <div>
                  <div class="flex items-center mb-6">
                    <div
                      class="w-20 h-20 bg-gradient-to-br from-blue-500 to-indigo-600 rounded-xl flex items-center justify-center mr-6">
                      <span class="text-white text-3xl font-bold">{{ selectedTool.icon }}</span>
                    </div>
                    <div>
                      <h3 class="text-2xl font-bold text-gray-900">{{ selectedTool.name }}</h3>
                      <p class="text-blue-600 font-medium">{{ selectedTool.category }}</p>
                      <p class="text-gray-500">{{ selectedTool.usage }}</p>
                    </div>
                  </div>
                  <p class="text-gray-600 leading-relaxed mb-6">{{ selectedTool.detailedDescription }}</p>
                  <div class="mb-6">
                    <h4 class="text-lg font-semibold text-gray-900 mb-3">Why I Use It</h4>
                    <p class="text-gray-600">{{ selectedTool.whyUse }}</p>
                  </div>
                </div>
                <div>
                  <h4 class="text-lg font-semibold text-gray-900 mb-4">Key Features</h4>
                  <ul class="space-y-3 mb-6">
                    <li v-for="feature in selectedTool.features" :key="feature" class="flex items-center text-gray-600">
                      <span class="text-green-500 mr-3">✓</span>
                      {{ feature }}
                    </li>
                  </ul>
                  <div class="mb-6">
                    <h4 class="text-lg font-semibold text-gray-900 mb-3">Learning Resources</h4>
                    <div class="space-y-2">
                      <a v-for="resource in selectedTool.resources" :key="resource" href="#"
                        class="block text-blue-600 hover:text-blue-800 transition-colors duration-200">
                        {{ resource }}
                      </a>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Services Section -->
      <section id="services" class="py-20 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="text-center mb-16">
            <span
              class="inline-block px-4 py-2 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mb-4">
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
              <div
                class="bg-white border border-gray-200 rounded-xl p-8 hover:border-blue-300 transition-all duration-300 hover:shadow-lg h-full">
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
                <button @click="scrollToSection('contact')"
                  class="w-full bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700 transition-all duration-300 shadow-lg">
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
                <div
                  class="bg-blue-600 text-white rounded-full w-16 h-16 flex items-center justify-center text-2xl font-bold mx-auto mb-6 group-hover:scale-110 transition-transform duration-300 shadow-lg">
                  {{ index + 1 }}
                </div>
                <h4 class="text-xl font-semibold text-gray-900 mb-3">{{ step.title }}</h4>
                <p class="text-gray-600 leading-relaxed">{{ step.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Portfolio Section -->
      <section id="portfolio" class="py-20 bg-gray-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="text-center mb-16">
            <span
              class="inline-block px-4 py-2 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mb-4">
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
              <div
                class="bg-white border border-gray-200 rounded-xl overflow-hidden hover:border-blue-300 transition-all duration-300 hover:shadow-lg transform hover:-translate-y-2">
                <div class="relative overflow-hidden">
                  <!-- Project Image Placeholder -->
                  <div
                    class="w-full h-48 bg-gradient-to-br from-blue-50 to-blue-100 flex items-center justify-center group-hover:scale-110 transition-transform duration-300">
                    <div class="text-center">
                      <div class="w-16 h-16 bg-blue-600 rounded-lg flex items-center justify-center mx-auto mb-2">
                        <span class="text-white font-bold">P</span>
                      </div>
                      <p class="text-blue-600 text-sm font-medium">Project</p>
                    </div>
                  </div>
                  <div
                    class="absolute inset-0 bg-black/50 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
                    <div class="flex space-x-4">
                      <button
                        class="bg-white text-gray-900 px-4 py-2 rounded-lg hover:bg-gray-100 transition-colors duration-200 font-medium">
                        View
                      </button>
                      <button
                        class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition-all duration-200 font-medium">
                        Live
                      </button>
                    </div>
                  </div>
                </div>
                <div class="p-6">
                  <div class="flex items-center justify-between mb-3">
                    <h3 class="text-xl font-semibold text-gray-900">{{ project.title }}</h3>
                    <span
                      class="px-3 py-1 bg-blue-50 border border-blue-200 text-blue-600 text-xs rounded-full font-medium">
                      {{ project.category }}
                    </span>
                  </div>
                  <p class="text-gray-600 mb-4 leading-relaxed">{{ project.description }}</p>
                  <div class="flex flex-wrap gap-2 mb-4">
                    <span v-for="tech in project.technologies" :key="tech"
                      class="px-2 py-1 bg-gray-100 text-gray-700 text-xs rounded-full hover:bg-blue-50 hover:text-blue-600 transition-colors duration-200">
                      {{ tech }}
                    </span>
                  </div>
                  <div class="flex items-center text-sm text-gray-500">
                    <span class="mr-2">📅</span>
                    {{ project.date }}
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Contact Section -->
      <section id="contact" class="py-20 bg-gradient-to-br from-gray-50 to-blue-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="text-center mb-16">
            <span
              class="inline-block px-4 py-2 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mb-4">
              Contact
            </span>
            <h2 class="text-4xl md:text-5xl font-bold mb-6 text-gray-900">
              Let's Connect
            </h2>
            <p class="text-xl text-gray-600 max-w-3xl mx-auto">
              I’m excited to collaborate on school projects or discuss new ideas—reach out today!
            </p>
          </div>

          <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
            <!-- Contact Form -->
            <div
              class="bg-white border border-gray-200 rounded-xl p-8 shadow-lg hover:shadow-xl transition-shadow duration-300">
              <h3 class="text-2xl font-semibold text-gray-900 mb-6">Send Me a Message</h3>
              <form @submit.prevent="submitForm" class="space-y-6">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                  <div>
                    <label for="firstName" class="block text-sm font-medium text-gray-700 mb-2">First Name</label>
                    <input type="text" id="firstName" v-model="form.firstName" required
                      class="w-full px-4 py-3 bg-white border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-600 focus:border-transparent text-gray-900 placeholder-gray-500 transition-colors duration-200"
                      placeholder="Sovan" />
                  </div>
                  <div>
                    <label for="lastName" class="block text-sm font-medium text-gray-700 mb-2">Last Name</label>
                    <input type="text" id="lastName" v-model="form.lastName" required
                      class="w-full px-4 py-3 bg-white border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-600 focus:border-transparent text-gray-900 placeholder-gray-500 transition-colors duration-200"
                      placeholder="Souern" />
                  </div>
                </div>
                <div>
                  <label for="email" class="block text-sm font-medium text-gray-700 mb-2">Email</label>
                  <input type="email" id="email" v-model="form.email" required
                    class="w-full px-4 py-3 bg-white border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-600 focus:border-transparent text-gray-900 placeholder-gray-500 transition-colors duration-200"
                    placeholder="sovan.souern@example.com" />
                </div>
                <div>
                  <label for="subject" class="block text-sm font-medium text-gray-700 mb-2">Subject</label>
                  <input type="text" id="subject" v-model="form.subject" required
                    class="w-full px-4 py-3 bg-white border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-600 focus:border-transparent text-gray-900 placeholder-gray-500 transition-colors duration-200"
                    placeholder="School Project Idea" />
                </div>
                <div>
                  <label for="message" class="block text-sm font-medium text-gray-700 mb-2">Message</label>
                  <textarea id="message" v-model="form.message" rows="6" required
                    class="w-full px-4 py-3 bg-white border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-600 focus:border-transparent text-gray-900 placeholder-gray-500 transition-colors duration-200 resize-none"
                    placeholder="Tell me about your project or idea..."></textarea>
                </div>
                <button type="submit" :disabled="isSubmitting"
                  class="w-full bg-blue-600 text-white py-4 rounded-lg font-semibold hover:bg-blue-700 transition-all duration-300 disabled:opacity-50 disabled:cursor-not-allowed shadow-lg">
                  <span v-if="isSubmitting">Sending...</span>
                  <span v-else>Send Message</span>
                </button>
                <div v-if="formSubmitted"
                  class="mt-6 p-4 bg-green-50 border border-green-200 text-green-700 rounded-lg text-center">
                  ✅ Thank you for your message! I’ll respond soon.
                </div>
              </form>
            </div>

            <!-- Contact Information & Social Links -->
            <div class="space-y-8">
              <!-- Contact Details -->
              <div
                class="bg-white border border-gray-200 rounded-xl p-8 shadow-lg hover:shadow-xl transition-shadow duration-300">
                <h3 class="text-2xl font-semibold text-gray-900 mb-6">Contact Details</h3>
                <div class="space-y-6">
                  <a href="mailto:sovan.souern@example.com" class="flex items-center group">
                    <div
                      class="w-12 h-12 bg-blue-600 rounded-lg flex items-center justify-center mr-4 group-hover:bg-blue-700 transition-all duration-300">
                      <svg class="w-6 h-6 text-white" fill="currentColor" viewBox="0 0 24 24">
                        <path
                          d="M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z" />
                      </svg>
                    </div>
                    <div>
                      <p class="font-medium text-gray-900">Email</p>
                      <p class="text-gray-600 hover:text-blue-600 transition-colors duration-300">
                        sovan.souern@example.com</p>
                    </div>
                  </a>
                  <a href="tel:+85512345678" class="flex items-center group">
                    <div
                      class="w-12 h-12 bg-blue-600 rounded-lg flex items-center justify-center mr-4 group-hover:bg-blue-700 transition-all duration-300">
                      <svg class="w-6 h-6 text-white" fill="currentColor" viewBox="0 0 24 24">
                        <path
                          d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z" />
                      </svg>
                    </div>
                    <div>
                      <p class="font-medium text-gray-900">Phone</p>
                      <p class="text-gray-600 hover:text-blue-600 transition-colors duration-300">+855 1234-5678</p>
                    </div>
                  </a>
                  <div class="flex items-center">
                    <div class="w-12 h-12 bg-blue-600 rounded-lg flex items-center justify-center mr-4">
                      <svg class="w-6 h-6 text-white" fill="currentColor" viewBox="0 0 24 24">
                        <path
                          d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z" />
                      </svg>
                    </div>
                    <div>
                      <p class="font-medium text-gray-900">Location</p>
                      <p class="text-gray-600">Phnom Penh, Cambodia</p>
                      <iframe
                        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3153.042166024858!2d104.8882156845673!3d11.56292917975771!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3106f5a9e9c7d1b7%3A0x6c6e95a7c1d5f0e0!2sPhnom%20Penh%2C%20Cambodia!5e0!3m2!1sen!2sus!4v1623456789!5m2!1sen!2sus"
                        width="100%" height="150" style="border:0;" allowfullscreen="" loading="lazy"
                        class="rounded-lg mt-4"></iframe>
                    </div>
                  </div>
                </div>
              </div>

              <!-- Social Links -->
              <div
                class="bg-white border border-gray-200 rounded-xl p-8 shadow-lg hover:shadow-xl transition-shadow duration-300">
                <h3 class="text-2xl font-semibold text-gray-900 mb-6">Follow Me</h3>
                <div class="flex space-x-4">
                  <!-- Telegram -->
                  <a href="https://t.me/yourtelegramusername" target="_blank" rel="noopener" class="group">
                    <div
                      class="w-12 h-12 bg-blue-600 rounded-lg flex items-center justify-center hover:bg-blue-700 transition-all duration-300 group-hover:scale-110 shadow-lg">
                      <svg class="w-6 h-6 text-white" fill="currentColor" viewBox="0 0 24 24">
                        <path
                          d="M9.993 16.2l-.396 3.51c.57 0 .816-.246 1.113-.543l2.67-2.547 5.535 4.035c1.014.558 1.74.264 1.995-.936l3.618-16.98c.33-1.53-.558-2.13-1.548-1.77l-21.06 8.1c-1.44.558-1.422 1.35-.246 1.71l5.385 1.68 12.495-7.89c.588-.384 1.125-.174.684.21l-10.125 9.15z" />
                      </svg>
                    </div>
                  </a>
                  <!-- Facebook -->
                  <a href="https://facebook.com/yourfacebookprofile" target="_blank" rel="noopener" class="group">
                    <div
                      class="w-12 h-12 bg-blue-600 rounded-lg flex items-center justify-center hover:bg-blue-700 transition-all duration-300 group-hover:scale-110 shadow-lg">
                      <svg class="w-6 h-6 text-white" fill="currentColor" viewBox="0 0 24 24">
                        <path
                          d="M22.675 0h-21.35c-.733 0-1.325.592-1.325 1.326v21.348c0 .733.592 1.326 1.325 1.326h11.495v-9.294h-3.124v-3.622h3.124v-2.672c0-3.1 1.893-4.788 4.659-4.788 1.325 0 2.463.099 2.797.143v3.24l-1.918.001c-1.504 0-1.797.715-1.797 1.763v2.313h3.587l-.467 3.622h-3.12v9.293h6.116c.733 0 1.325-.593 1.325-1.326v-21.349c0-.734-.592-1.326-1.325-1.326z" />
                      </svg>
                    </div>
                  </a>
                  <!-- LinkedIn -->
                  <a href="https://linkedin.com/in/yourlinkedinprofile" target="_blank" rel="noopener" class="group">
                    <div
                      class="w-12 h-12 bg-blue-600 rounded-lg flex items-center justify-center hover:bg-blue-700 transition-all duration-300 group-hover:scale-110 shadow-lg">
                      <svg class="w-6 h-6 text-white" fill="currentColor" viewBox="0 0 24 24">
                        <path
                          d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-1.337-.025-3.05-1.864-3.05-1.865 0-2.149 1.451-2.149 2.956v5.698h-3v-11h2.881v1.518h.041c.401-.764 1.382-1.864 2.841-1.864 3.038 0 3.6 1.996 3.6 4.588v6.758z" />
                      </svg>
                    </div>
                  </a>
                </div>
              </div>


            </div>
          </div>
        </div>
      </section>
    </main>

    <!-- Footer -->
    <footer class="bg-white border-t border-gray-200 py-12">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
          <div class="col-span-1 md:col-span-2">
            <div class="flex items-center mb-4">
              <div class="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center mr-3">
                <span class="text-white font-bold text-lg">JD</span>
              </div>
              <span class="text-xl font-bold text-gray-900">
                Sovan Souern
              </span>
            </div>
            <p class="text-gray-600 mb-6 leading-relaxed max-w-md">
              WEB Developer passionate about creating amazing digital experiences that make a difference in the
              world.
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
              <li><button @click="scrollToSection('home')"
                  class="text-gray-600 hover:text-blue-600 transition-colors duration-200">Home</button></li>
              <li><button @click="scrollToSection('about')"
                  class="text-gray-600 hover:text-blue-600 transition-colors duration-200">About</button></li>
              <li><button @click="scrollToSection('skills')"
                  class="text-gray-600 hover:text-blue-600 transition-colors duration-200">Skills</button></li>
              <li><button @click="scrollToSection('services')"
                  class="text-gray-600 hover:text-blue-600 transition-colors duration-200">Services</button></li>
              <li><button @click="scrollToSection('portfolio')"
                  class="text-gray-600 hover:text-blue-600 transition-colors duration-200">Portfolio</button></li>
              <li><button @click="scrollToSection('contact')"
                  class="text-gray-600 hover:text-blue-600 transition-colors duration-200">Contact</button></li>
            </ul>
          </div>
          <div>
            <h4 class="text-lg font-semibold text-gray-900 mb-4">Contact</h4>
            <ul class="space-y-2 text-gray-600">
              <li>sovan.souern@student.passerellesnumeriques.org</li>
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
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

// Navigation and scroll tracking
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

// Skills & Tools Tab Management
const activeTab = ref('skills')
const selectedSkillCategory = ref('All')
const selectedSkill = ref(null)
const selectedToolCategory = ref('All')
const selectedTool = ref(null)

// Smooth scroll to section
const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

// Track active section on scroll
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

// Enhanced Skills data with more technologies
const skillCategories = ['All', 'Frontend', 'Backend', 'Database', 'Programming', 'Styling', 'Tools']

const skills = [
  // Frontend Technologies
  {
    name: 'HTML & CSS',
    category: 'Frontend',
    experience: '3+ years',
    icon: 'H',
    image: '/images/skills/html5.png',
    description: 'Semantic HTML5 and modern CSS3 with responsive design principles',
    projects: ['Personal Portfolio', 'Restaurant Website', 'E-commerce Landing Page'],
    tools: ['VS Code', 'Chrome DevTools', 'Figma', 'CodePen']
  },
  {
    name: 'JavaScript',
    category: 'Frontend',
    experience: '2+ years',
    icon: 'JS',
    image: '/images/skills/javascript.png',
    description: 'Modern ES6+ JavaScript with DOM manipulation and async programming',
    projects: ['Todo App', 'Weather App', 'Interactive Calculator'],
    tools: ['VS Code', 'Node.js', 'Chrome DevTools', 'Babel']
  },
  {
    name: 'TypeScript',
    category: 'Frontend',
    experience: '1+ year',
    icon: 'TS',
    image: '/images/skills/typescript.png',
    description: 'Strongly typed JavaScript for better code quality and development experience',
    projects: ['Type-safe React Apps', 'Angular Projects', 'Node.js APIs'],
    tools: ['VS Code', 'TSC', 'ESLint', 'Prettier']
  },
  {
    name: 'Vue.js',
    category: 'Frontend',
    experience: '1.5+ years',
    icon: 'V',
    image: '/images/skills/vuejs.png',
    description: 'Progressive JavaScript framework for building user interfaces',
    projects: ['Portfolio Website', 'Task Management App', 'Blog Platform'],
    tools: ['Vue CLI', 'Vite', 'Vue DevTools', 'Pinia']
  },
  {
    name: 'React',
    category: 'Frontend',
    experience: '1+ year',
    icon: 'R',
    image: '/images/skills/react.png',
    description: 'Popular JavaScript library for building component-based UIs',
    projects: ['Learning Projects', 'Component Library', 'Simple SPA'],
    tools: ['Create React App', 'React DevTools', 'Redux', 'Next.js']
  },
  // Backend Technologies
  {
    name: 'PHP',
    category: 'Backend',
    experience: '2+ years',
    icon: 'P',
    image: '/images/skills/php.png',
    description: 'Server-side scripting language for web development',
    projects: ['School Management System', 'Blog CMS', 'API Development'],
    tools: ['XAMPP', 'Composer', 'PHPStorm', 'Laravel']
  },
  {
    name: 'Laravel',
    category: 'Backend',
    experience: '1.5+ years',
    icon: 'L',
    image: '/images/skills/laravel.png',
    description: 'Elegant PHP framework for web artisans',
    projects: ['E-commerce Platform', 'Student Portal', 'REST API'],
    tools: ['Artisan', 'Eloquent ORM', 'Blade Templates', 'Laravel Mix']
  },
  {
    name: 'Node.js',
    category: 'Backend',
    experience: '1+ year',
    icon: 'N',
    image: '/images/skills/nodejs.png',
    description: 'JavaScript runtime for server-side development',
    projects: ['REST API', 'Real-time Chat App', 'File Upload Service'],
    tools: ['npm', 'Express.js', 'Nodemon', 'PM2']
  },
  // Programming Languages
  {
    name: 'Python',
    category: 'Programming',
    experience: '1+ year',
    icon: 'Py',
    image: '/images/skills/python.png',
    description: 'Versatile programming language for algorithms, data science, and web development',
    projects: ['Algorithm Solutions', 'Data Analysis Scripts', 'Automation Tools'],
    tools: ['PyCharm', 'Jupyter', 'pip', 'virtualenv']
  },
  {
    name: 'Algorithms & DSA',
    category: 'Programming',
    experience: '1+ year',
    icon: 'A',
    image: '/images/skills/code.png',
    description: 'Data Structures and Algorithms problem solving with Python',
    projects: ['LeetCode Solutions', 'Sorting Algorithms', 'Graph Problems'],
    tools: ['Python', 'LeetCode', 'HackerRank', 'CodeWars']
  },
  {
    name: 'OOP Concepts',
    category: 'Programming',
    experience: '2+ years',
    icon: 'O',
    image: '/images/skills/oop.png',
    description: 'Object-Oriented Programming principles and design patterns',
    projects: ['Class-based Applications', 'Design Patterns', 'Clean Architecture'],
    tools: ['PHP', 'JavaScript', 'Python', 'TypeScript']
  },
  // Database Technologies
  {
    name: 'MySQL',
    category: 'Database',
    experience: '2+ years',
    icon: 'M',
    image: '/images/skills/mysql.png',
    description: 'Relational database management system',
    projects: ['School Database', 'E-commerce DB', 'User Management System'],
    tools: ['phpMyAdmin', 'MySQL Workbench', 'HeidiSQL', 'Sequel Pro']
  },
  {
    name: 'MongoDB',
    category: 'Database',
    experience: '6+ months',
    icon: 'Mo',
    image: '/images/skills/mongodb.png',
    description: 'NoSQL document-oriented database',
    projects: ['Blog API', 'User Profiles', 'Content Management'],
    tools: ['MongoDB Compass', 'Mongoose', 'Atlas', 'Robo 3T']
  },
  // Styling Technologies
  {
    name: 'Tailwind CSS',
    category: 'Styling',
    experience: '1+ year',
    icon: 'T',
    image: '/images/skills/tailwindcss.png',
    description: 'Utility-first CSS framework for rapid UI development',
    projects: ['Modern Portfolio', 'Dashboard UI', 'Landing Pages'],
    tools: ['Tailwind CLI', 'Headless UI', 'Tailwind Play', 'VS Code Extension']
  },
  {
    name: 'Bootstrap 5',
    category: 'Styling',
    experience: '2+ years',
    icon: 'B',
    image: '/images/skills/bootstrap.png',
    description: 'Popular CSS framework for responsive web development',
    projects: ['Early Projects', 'Admin Dashboards', 'Business Websites'],
    tools: ['Bootstrap CDN', 'Bootstrap Studio', 'Sass', 'jQuery']
  },
  {
    name: 'Sass',
    category: 'Styling',
    experience: '1.5+ years',
    icon: 'S',
    image: '/images/skills/sass.png',
    description: 'CSS preprocessor with variables, nesting, and mixins',
    projects: ['Custom Themes', 'Component Libraries', 'Design Systems'],
    tools: ['VS Code', 'Sass CLI', 'Webpack', 'Gulp']
  },
  // Development Tools
  {
    name: 'Git & GitHub',
    category: 'Tools',
    experience: '2+ years',
    icon: 'G',
    image: '/images/skills/git.png',
    description: 'Version control system and code collaboration platform',
    projects: ['All Projects', 'Open Source Contributions', 'Team Collaborations'],
    tools: ['Git CLI', 'GitHub Desktop', 'VS Code Git', 'GitKraken']
  }
]

const filteredSkills = computed(() => {
  if (selectedSkillCategory.value === 'All') {
    return skills
  }
  return skills.filter(skill => skill.category === selectedSkillCategory.value)
})

const selectSkill = (skill) => {
  selectedSkill.value = skill
}

// Enhanced Tools data with more tools
const toolCategories = ['All', 'Code Editors', 'Design Tools', 'Learning Platforms', 'Development Tools', 'Project Management']

const tools = [
  // Code Editors
  {
    name: 'Visual Studio Code',
    category: 'Code Editors',
    icon: 'VS',
    usage: 'Daily Use',
    description: 'Primary code editor for all development work',
    detailedDescription: 'VS Code is my main development environment. I use it for all programming languages and have customized it with extensions for maximum productivity.',
    whyUse: 'Excellent IntelliSense, integrated terminal, Git integration, and vast extension marketplace make it perfect for web development.',
    features: [
      'Intelligent code completion',
      'Built-in Git integration',
      'Integrated terminal',
      'Extension marketplace',
      'Live Share collaboration',
      'Debugging support'
    ],
    resources: [
      'VS Code Documentation',
      'Extension Marketplace',
      'Keyboard Shortcuts Guide',
      'Settings Sync'
    ]
  },
  // Design Tools
  {
    name: 'Figma',
    category: 'Design Tools',
    icon: 'F',
    usage: 'Regular Use',
    description: 'UI/UX design and prototyping tool',
    detailedDescription: 'Use Figma for designing user interfaces, creating wireframes, and collaborating with designers. Essential for planning projects before coding.',
    whyUse: 'Browser-based, real-time collaboration, component systems, and developer handoff features make it ideal for web design.',
    features: [
      'Real-time collaboration',
      'Component libraries',
      'Prototyping tools',
      'Developer handoff',
      'Version history',
      'Plugin ecosystem'
    ],
    resources: [
      'Figma Academy',
      'Design System Templates',
      'Community Resources',
      'Plugin Directory'
    ]
  },
  // Development Tools
  {
    name: 'Chrome DevTools',
    category: 'Development Tools',
    icon: 'C',
    usage: 'Daily Use',
    description: 'Browser developer tools for debugging and optimization',
    detailedDescription: 'Essential for debugging JavaScript, inspecting HTML/CSS, monitoring network requests, and optimizing web performance.',
    whyUse: 'Built into Chrome, comprehensive debugging features, performance profiling, and mobile device simulation.',
    features: [
      'Element inspector',
      'JavaScript debugger',
      'Network monitoring',
      'Performance profiling',
      'Mobile simulation',
      'Console logging'
    ],
    resources: [
      'DevTools Documentation',
      'Performance Tips',
      'Debugging Guide',
      'Mobile Testing'
    ]
  },
  {
    name: 'XAMPP',
    category: 'Development Tools',
    icon: 'X',
    usage: 'Local Development',
    description: 'Local development environment for PHP projects',
    detailedDescription: 'XAMPP provides Apache, MySQL, PHP, and Perl in one package. Perfect for local PHP development and testing.',
    whyUse: 'Easy setup, includes everything needed for PHP development, cross-platform, and great for learning server-side development.',
    features: [
      'Apache web server',
      'MySQL database',
      'PHP interpreter',
      'phpMyAdmin',
      'Easy configuration',
      'Cross-platform'
    ],
    resources: [
      'XAMPP Documentation',
      'PHP Configuration',
      'MySQL Setup',
      'Virtual Hosts Guide'
    ]
  },
  {
    name: 'Postman',
    category: 'Development Tools',
    icon: 'Po',
    usage: 'API Testing',
    description: 'API development and testing platform',
    detailedDescription: 'Essential tool for testing APIs, documenting endpoints, and collaborating on API development projects.',
    whyUse: 'User-friendly interface, comprehensive testing features, collaboration tools, and excellent documentation generation.',
    features: [
      'API testing',
      'Request collections',
      'Environment variables',
      'Automated testing',
      'Documentation generation',
      'Team collaboration'
    ],
    resources: [
      'Postman Learning Center',
      'API Testing Guide',
      'Collection Templates',
      'Automation Scripts'
    ]
  },
  // Learning Platforms
  {
    name: 'YouTube',
    category: 'Learning Platforms',
    icon: 'Y',
    usage: 'Daily Learning',
    description: 'Primary platform for learning new technologies',
    detailedDescription: 'YouTube is my go-to platform for learning programming concepts, following tutorials, and staying updated with latest technologies.',
    whyUse: 'Free access to high-quality programming tutorials, diverse teaching styles, and up-to-date content from experienced developers.',
    features: [
      'Free programming tutorials',
      'Multiple teaching styles',
      'Latest technology updates',
      'Community discussions',
      'Playlist organization',
      'Offline viewing'
    ],
    resources: [
      'Traversy Media',
      'The Net Ninja',
      'Academind',
      'FreeCodeCamp'
    ]
  },
  {
    name: 'freeCodeCamp',
    category: 'Learning Platforms',
    icon: 'fC',
    usage: 'Regular Learning',
    description: 'Comprehensive coding curriculum and certifications',
    detailedDescription: 'Structured learning path for web development with hands-on projects and certifications. Great for systematic learning.',
    whyUse: 'Free, comprehensive curriculum, hands-on projects, certifications, and supportive community.',
    features: [
      'Structured curriculum',
      'Hands-on projects',
      'Free certifications',
      'Community support',
      'Real-world projects',
      'Interview preparation'
    ],
    resources: [
      'Responsive Web Design',
      'JavaScript Algorithms',
      'Frontend Libraries',
      'Backend Development'
    ]
  },
  {
    name: 'LeetCode',
    category: 'Learning Platforms',
    icon: 'LC',
    usage: 'Algorithm Practice',
    description: 'Platform for practicing coding problems and algorithms',
    detailedDescription: 'Essential for improving problem-solving skills and preparing for technical interviews with algorithmic challenges.',
    whyUse: 'Comprehensive problem set, multiple difficulty levels, discussion forums, and interview preparation focus.',
    features: [
      'Coding challenges',
      'Algorithm practice',
      'Interview preparation',
      'Discussion forums',
      'Progress tracking',
      'Company-specific problems'
    ],
    resources: [
      'LeetCode Explore',
      'Interview Preparation Kit',
      'Algorithm Study Plans',
      'Discussion Solutions'
    ]
  },
  // Project Management
  {
    name: 'Jira',
    category: 'Project Management',
    icon: 'J',
    usage: 'Team Projects',
    description: 'Agile project management and issue tracking tool',
    detailedDescription: 'Used for managing development projects, tracking bugs, planning sprints, and collaborating with team members in agile environments.',
    whyUse: 'Industry-standard tool for agile development, excellent for sprint planning, issue tracking, and team collaboration.',
    features: [
      'Sprint planning',
      'Issue tracking',
      'Agile boards',
      'Reporting & analytics',
      'Team collaboration',
      'Integration with dev tools'
    ],
    resources: [
      'Jira Documentation',
      'Agile Best Practices',
      'Scrum Guide',
      'Project Templates'
    ]
  },
  {
    name: 'Notion',
    category: 'Project Management',
    icon: 'No',
    usage: 'Documentation',
    description: 'All-in-one workspace for notes, docs, and project management',
    detailedDescription: 'Use Notion for project documentation, note-taking, knowledge management, and personal productivity organization.',
    whyUse: 'Flexible workspace that combines notes, databases, kanban boards, and wikis in one platform.',
    features: [
      'Rich text editing',
      'Database management',
      'Template library',
      'Team collaboration',
      'API integration',
      'Cross-platform sync'
    ],
    resources: [
      'Notion Academy',
      'Template Gallery',
      'Community Resources',
      'API Documentation'
    ]
  }
]

const filteredTools = computed(() => {
  if (selectedToolCategory.value === 'All') {
    return tools
  }
  return tools.filter(tool => tool.category === selectedToolCategory.value)
})

const selectTool = (tool) => {
  selectedTool.value = tool
}

// Experience data
const experience = [
  {
    id: 1,
    position: 'Backend Developer',
    company: '',
    period: '2025 - Present',
    description: 'Lead development of enterprise web applications, mentor junior developers, and architect scalable solutions using modern technologies. Responsible for code reviews, technical decisions, and project planning.',
    technologies: ['Node.js', 'AWS', 'Deploy', 'MySQL', 'TypeScript']
  },
  {
    id: 2,
    position: 'Frontend Developer',
    company: '',
    period: '2025 - Present',
    description: 'Developed responsive web applications and improved user experience across multiple client projects. Collaborated with designers and backend developers to deliver high-quality solutions.',
    technologies: ['Vue.js', 'JavaScript', 'SASS', 'Firebase', 'Figma']
  },
  {
    id: 3,
    position: 'Web Developer',
    company: '',
    period: 'Apply for Internship',
    description: 'Built and maintained web applications while learning best practices in software development. Participated in agile development processes and contributed to open-source projects.',
    technologies: ['HTML', 'CSS', 'JavaScript', 'PHP', 'MySQL', 'Git']
  }
]

// Services data
const services = [
  {
    id: 1,
    title: 'Web Development',
    description: 'Custom web applications built with modern technologies and best practices for optimal performance and user experience.',
    features: ['Responsive Design', 'Performance Optimization', 'SEO Friendly', 'Cross-browser Compatible', 'Modern Frameworks'],
    price: 'From $2,500'
  },
  {
    id: 2,
    title: 'Mobile Development',
    description: 'Native and cross-platform mobile applications for iOS and Android with seamless user experiences.',
    features: ['iOS & Android', 'React Native', 'App Store Deployment', 'Push Notifications', 'Offline Support'],
    price: 'From $3,500'
  },
  {
    id: 3,
    title: 'E-Commerce Solutions',
    description: 'Complete online store development with payment integration, inventory management, and analytics.',
    features: ['Payment Integration', 'Inventory Management', 'Admin Dashboard', 'Analytics', 'Security'],
    price: 'From $4,000'
  },
  {
    id: 4,
    title: 'UI/UX Design',
    description: 'User-centered design for web and mobile applications that prioritize usability and aesthetics.',
    features: ['User Research', 'Wireframing', 'Prototyping', 'Design Systems', 'Usability Testing'],
    price: 'From $1,500'
  },
  {
    id: 5,
    title: 'API Development',
    description: 'RESTful APIs and backend services with robust architecture, security, and documentation.',
    features: ['Database Design', 'Authentication', 'Documentation', 'Testing', 'Scalability'],
    price: 'From $2,000'
  },
  {
    id: 6,
    title: 'Consulting',
    description: 'Technical consulting and code review services to improve your development processes and code quality.',
    features: ['Architecture Review', 'Performance Audit', 'Best Practices', 'Team Training', 'Strategy Planning'],
    price: 'From $150/hr'
  }
]

// Process data
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

// Portfolio data
const selectedCategory = ref('All')
const portfolioCategories = ['All', 'Web Apps', 'Mobile Apps', 'E-Commerce', 'Landing Pages', 'UI/UX Design']

const portfolioProjects = [
  {
    id: 1,
    title: 'Sports Website',
    description: 'A modern, responsive sports website showcasing teams, events, and schedules with a sleek design crafted using Sass for advanced styling.',
    category: 'Landing Pages',
    technologies: ['HTML', 'CSS', 'Sass', 'Figma', 'Git', 'GitHub'],
    date: 'May 2025'
  },
  {
    id: 2,
    title: 'Weather App',
    description: 'An interactive web application that fetches real-time weather data using a public Weather API, featuring dynamic UI and responsive design.',
    category: 'Web Apps',
    technologies: ['JavaScript', 'HTML', 'CSS', 'Weather API', 'Git', 'GitHub'],
    date: 'April 2025'
  },
  {
    id: 3,
    title: 'System Management Tool',
    description: 'A Python-based management tool leveraging algorithms for efficient task automation, deployed on AWS EC2 for scalability and reliability.',
    category: 'Web Apps',
    technologies: ['Python', 'Algorithms', 'AWS EC2', 'Git', 'GitHub'],
    date: 'March 2025'
  },
  {
    id: 4,
    title: 'E-Commerce Website',
    description: 'A full-featured e-commerce platform with an integrated Point of Sale system, built using PHP and MVC architecture for maintainability.',
    category: 'E-Commerce',
    technologies: ['PHP', 'MVC', 'MySQL', 'HTML', 'CSS', 'Git', 'GitHub', 'Bootstrap', 'Jira'],
    date: 'February 2025'
  },
  {
    id: 5,
    title: 'Task Management App',
    description: 'An object-oriented application management system designed with clean architecture principles to streamline app lifecycle processes.',
    category: 'Web Apps',
    technologies: ['OOP', 'Git', 'GitHub'],
    date: 'January 2025'
  },
]

const filteredProjects = computed(() => {
  if (selectedCategory.value === 'All') {
    return portfolioProjects
  }
  return portfolioProjects.filter(project => project.category === selectedCategory.value)
})

// Contact form
const form = ref({
  firstName: '',
  lastName: '',
  email: '',
  subject: '',
  message: ''
})

const isSubmitting = ref(false)
const formSubmitted = ref(false)

const submitForm = async () => {
  isSubmitting.value = true
  // Simulate form submission
  await new Promise(resolve => setTimeout(resolve, 2000))
  formSubmitted.value = true
  isSubmitting.value = false
  // Reset form
  form.value = {
    firstName: '',
    lastName: '',
    email: '',
    subject: '',
    message: ''
  }
  // Hide success message after 5 seconds
  setTimeout(() => {
    formSubmitted.value = false
  }, 5000)
}
</script>

<style scoped>
/* Custom scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f5f9;
}

::-webkit-scrollbar-thumb {
  background: #3b82f6;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: #2563eb;
}

/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Focus styles */
:focus {
  outline: 2px solid #3b82f6;
  outline-offset: 2px;
}

/* Skill image styles */
.skill-image {
  transition: transform 0.3s ease;
}

.skill-image:hover {
  transform: scale(1.1);
  /* Slight zoom on hover */
}

.skill-icon-container {
  background: #ffffff;
  /* White background for logo contrast */
  border: 1px solid #e5e7eb;
  /* Subtle border */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
  /* Light shadow */
}

img[src$=".svg"] {
  filter: none;
  /* Preserve original SVG colors */
}
</style>