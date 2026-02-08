<template>
  <section id="about" class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16">
        <span class="inline-block px-4 py-2 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mb-4">
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
          <div class="relative flex items-center justify-center w-full h-96 rounded-2xl bg-white shadow-lg hover:shadow-xl transition-shadow duration-300 overflow-hidden">
            <img src="@/assets/image/photo_2025-05-26_09-25-06.jpg" alt="About Me Full Image" class="object-contain w-full h-full transition-transform duration-300 hover:scale-105" />
          </div>
        </div>
        <div>
          <h3 class="text-3xl font-bold mb-6 text-gray-900">My Story</h3>
          <div class="space-y-6 text-gray-600 leading-relaxed">
            <p>
              I'm a student passionate about web development, exploring this field through school projects. My journey began with curiosity about how websites are built, sparking my interest in coding and design.
            </p>
            <p>
              I’m learning modern web technologies like React, Vue.js, HTML, and CSS through my coursework. I enjoy creating projects that are functional and aim to improve my skills with each assignment.
            </p>
            <p>
              Outside of school, I love experimenting with new tools, working on personal coding projects, and learning from online resources to grow my knowledge.
            </p>
          </div>
          <button @click="scrollToSection('contact')" class="mt-8 bg-blue-600 text-white px-8 py-3 rounded-lg font-semibold hover:bg-blue-700 transition-all duration-300 shadow-lg">
            Let's Work Together
          </button>
        </div>
      </div>

      <!-- Experience Timeline -->
      <div>
        <h3 class="text-3xl font-bold text-center mb-12 text-gray-900">Professional Experience</h3>
        <div class="space-y-8">
          <div v-for="exp in experience" :key="exp.id" class="group">
            <div class="bg-white border border-gray-200 rounded-xl p-8 hover:border-blue-300 transition-all duration-300 hover:shadow-lg">
              <div class="flex flex-col md:flex-row md:items-center md:justify-between mb-4">
                <div>
                  <h4 class="text-xl font-semibold text-gray-900 mb-1">{{ exp.position }}</h4>
                  <p class="text-blue-600 font-medium">{{ exp.company }}</p>
                </div>
                <span class="inline-block px-3 py-1 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mt-2 md:mt-0">
                  {{ exp.period }}
                </span>
              </div>
              <p class="text-gray-600 mb-4 leading-relaxed">{{ exp.description }}</p>
              <div class="flex flex-wrap gap-2">
                <span v-for="tech in exp.technologies" :key="tech" class="px-3 py-1 bg-gray-100 text-gray-700 text-sm rounded-full hover:bg-blue-50 hover:text-blue-600 transition-colors duration-200">
                  {{ tech }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const experience = [
  {
    id: 1,
    position: 'Backend Developer',
    company: '',
    period: '2025 - Present',
    description: 'Lead development of enterprise web applications, mentor junior developers, and architect scalable solutions using modern technologies. Responsible for code reviews, technical decisions, and project planning.',
    technologies: ['Laravel','PHP','Node.js', 'AWS', 'Deploy', 'MySQL', 'TypeScript','Python','MysQL']
  },
  {
    id: 2,
    position: 'Frontend Developer',
    company: '',
    period: '2025 - Present',
    description: 'Developed responsive web applications and improved user experience across multiple client projects. Collaborated with designers and backend developers to deliver high-quality solutions.',
    technologies: ['Vue.js','Tailwind CSS','Boostrap5','JavaScript', 'SASS', 'Firebase', 'Figma']
  },
  {
    id: 3,
    position: 'Web Developer',
    company: '',
    period: 'Apply for Internship',
    description: 'Built and maintained web applications while learning best practices in software development. Participated in agile development processes and contributed to open-source projects.',
    technologies: ['Laravel','Python','PHP','OOP Typescript','VueJS','Node JS','HTML', 'CSS', 'JavaScript', 'Tailwind CSS','Boostrap5', 'MySQL', 'Git','WordPress','Figma', 'Firebase']
  },
  {
    id: 4,
    position: 'Data Analyst',
    company: '',
    period: '2 months',
    description: 'Analyzes data to identify trends and insights that inform business decisions. Utilizes tools like Excel, Power BI.',
    technologies: ['Power BI','Excel','Data Visualization', 'Data Cleaning', 'Python']
  }
]

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>