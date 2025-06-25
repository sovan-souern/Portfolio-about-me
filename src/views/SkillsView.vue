<template>
  <section id="skills" class="py-20 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16">
        <span class="inline-block px-4 py-2 bg-blue-50 border border-blue-200 rounded-full text-blue-600 text-sm font-medium mb-4">
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
          <button v-for="category in skillCategories" :key="category" @click="selectedSkillCategory = category" :class="[
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
          <div v-for="skill in filteredSkills" :key="skill.name" class="group cursor-pointer" @click="selectSkill(skill)">
            <div class="bg-white border border-gray-200 rounded-xl p-6 hover:border-blue-300 transition-all duration-300 hover:shadow-lg transform hover:-translate-y-2 h-full">
              <div class="flex items-center mb-4">
                <div class="w-12 h-12 bg-white border border-gray-200 rounded-lg flex items-center justify-center mr-4 p-1 skill-icon-container">
                  <img v-if="skill.image" :src="skill.image" :alt="`Logo for ${skill.name}`" class="w-full h-full object-contain skill-image" @error="skill.image = null">
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
                <span class="inline-block px-3 py-1 bg-blue-50 text-blue-600 text-xs rounded-full font-medium border border-blue-200">
                  {{ skill.experience }}
                </span>
              </div>
              <!-- Tools Used -->
              <div class="flex flex-wrap gap-2">
                <span v-for="tool in skill.tools?.slice(0, 2)" :key="tool" class="px-2 py-1 bg-gray-100 text-gray-600 text-xs rounded-full hover:bg-blue-50 hover:text-blue-600 transition-colors duration-200">
                  {{ tool }}
                </span>
                <span v-if="skill.tools?.length > 2" class="px-2 py-1 bg-gray-100 text-gray-600 text-xs rounded-full">
                  +{{ skill.tools.length - 2 }}
                </span>
              </div>
            </div>
          </div>
        </div>

        <!-- Selected Skill Detail -->
        <div v-if="selectedSkill" class="bg-white border border-gray-200 rounded-2xl p-8 shadow-lg">
          <div class="text-center mb-6">
            <div class="w-20 h-20 bg-white border border-gray-200 rounded-xl flex items-center justify-center mx-auto mb-4 p-2 skill-icon-container">
              <img v-if="selectedSkill.image" :src="selectedSkill.image" :alt="`Logo for ${selectedSkill.name}`" class="w-full h-full object-contain skill-image" @error="selectedSkill.image = null">
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
                <span v-for="tool in selectedSkill.tools" :key="tool" class="px-3 py-1 bg-blue-50 text-blue-600 text-sm rounded-full border border-blue-200">
                  {{ tool }}
                </span>
              </div>
            </div>
            <div>
              <h4 class="text-lg font-semibold text-gray-900 mb-4">Projects Built</h4>
              <ul class="space-y-2">
                <li v-for="project in selectedSkill.projects" :key="project" class="flex items-center text-gray-600">
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
          <button v-for="category in toolCategories" :key="category" @click="selectedToolCategory = category" :class="[
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
          <div v-for="tool in filteredTools" :key="tool.name" class="group cursor-pointer" @click="selectTool(tool)">
            <div class="bg-white border border-gray-200 rounded-xl p-6 hover:border-blue-300 transition-all duration-300 hover:shadow-lg transform hover:-translate-y-2 h-full">
              <div class="flex items-center mb-4">
                <div class="w-16 h-16 bg-white border border-gray-200 rounded-xl flex items-center justify-center mr-4 p-2">
                  <img v-if="tool.image" :src="tool.image" :alt="`Logo for ${tool.name}`" class="w-full h-full object-contain" @error="tool.image = null">
                  <div v-else class="w-full h-full bg-gradient-to-br from-blue-500 to-indigo-600 rounded-lg flex items-center justify-center">
                    <span class="text-white text-xl font-bold">{{ tool.icon }}</span>
                  </div>
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
                <div v-for="feature in tool.features.slice(0, 2)" :key="feature" class="flex items-center text-sm text-gray-600">
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
                <div class="w-20 h-20 bg-white border border-gray-200 rounded-xl flex items-center justify-center mr-6 p-2">
                  <img v-if="selectedTool.image" :src="selectedTool.image" :alt="`Logo for ${selectedTool.name}`" class="w-full h-full object-contain" @error="selectedTool.image = null">
                  <div v-else class="w-full h-full bg-gradient-to-br from-blue-500 to-indigo-600 rounded-lg flex items-center justify-center">
                    <span class="text-white text-3xl font-bold">{{ selectedTool.icon }}</span>
                  </div>
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
                  <a v-for="resource in selectedTool.resources" :key="resource" href="#" class="block text-blue-600 hover:text-blue-800 transition-colors duration-200">
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
</template>

<script setup>
import { ref, computed } from 'vue'

const activeTab = ref('skills')
const selectedSkillCategory = ref('All')
const selectedSkill = ref(null)
const selectedToolCategory = ref('All')
const selectedTool = ref(null)

const skillCategories = ['All', 'Frontend', 'Backend', 'Database', 'Programming', 'Styling']

const skills = [
  // Frontend Technologies
  {
    name: 'HTML & CSS',
    category: 'Frontend',
    experience: '1+ years',
    image: 'https://i.pinimg.com/736x/aa/b3/01/aab301aaa113a8610a6fe4ef6cb4e382.jpg',
    description: 'Semantic HTML5 and modern CSS3 with responsive design principles',
    projects: ['Personal Portfolio', 'Restaurant Website', 'E-commerce Landing Page'],
    tools: ['VS Code', 'Chrome DevTools', 'Figma', 'CodePen']
  },
  {
    name: 'JavaScript',
    category: 'Frontend',
    experience: '1+ years',
    image: 'https://i.pinimg.com/736x/0e/4f/dc/0e4fdce8ac22e09688c580e5bc4dcd7d.jpg',
    description: 'Modern ES6+ JavaScript with DOM manipulation and async programming',
    projects: ['Todo App', 'Weather App', 'Interactive Calculator'],
    tools: ['VS Code', 'Node.js', 'Chrome DevTools', 'Babel']
  },
  {
    name: 'OOP TypeScript',
    category: 'Frontend',
    experience: '2+ months',
    image: 'https://i.pinimg.com/736x/66/d5/23/66d5238900aab3d7b86dc5e53a77c817.jpg',
    description: 'Strongly typed JavaScript for better code quality and development experience',
    projects: ['Type-safe React Apps', 'Angular Projects', 'Node.js APIs'],
    tools: ['VS Code', 'TSC', 'ESLint', 'Prettier']
  },
  {
    name: 'Vue.js',
    category: 'Frontend',
    experience: 'studying 1+ month',
    image: 'https://i.pinimg.com/736x/c5/5f/50/c55f50cb7be3c17582cc0e28f961fe56.jpg',
    description: 'Progressive JavaScript framework for building user interfaces',
    projects: ['Portfolio Website', 'Task Management App', 'Blog Platform'],
    tools: ['Vue CLI', 'Vite', 'Vue DevTools', 'Pinia']
  },

  // Backend Technologies
  {
    name: 'PHP',
    category: 'Backend',
    experience: '4+ months',
    image: 'https://i.pinimg.com/736x/1b/29/a5/1b29a538acb3efa07b2289d932b2daa9.jpg',
    description: 'Server-side scripting language for web development',
    projects: ['School Management System', 'Blog CMS', 'API Development'],
    tools: ['XAMPP', 'Composer', 'PHPStorm', 'Laravel']
  },
  {
    name: 'Laravel',
    category: 'Backend',
    experience: 'studying 1+ month',
    image: 'https://i.pinimg.com/736x/ed/94/e3/ed94e3e6fae5dd09cd8f7652f4a01c3d.jpg',
    description: 'Elegant PHP framework for web artisans',
    projects: ['E-commerce Platform', 'Student Portal', 'REST API'],
    tools: ['Artisan', 'Eloquent ORM', 'Blade Templates', 'Laravel Mix']
  },
  {
    name: 'Node.js',
    category: 'Backend',
    experience: '3 months',
    image: 'https://i.pinimg.com/736x/a4/22/c1/a422c15025eb156516c67e0bbdd2f382.jpg',
    description: 'JavaScript runtime for server-side development',
    projects: ['REST API', 'Real-time Chat App', 'File Upload Service'],
    tools: ['npm', 'Express.js', 'Nodemon', 'PM2']
  },
  // Programming Languages
  {
    name: 'Python',
    category: 'Programming',
    experience: '1+ year',
    image: 'https://i.pinimg.com/736x/ed/66/63/ed666327dd3ce274d94f2b3547155891.jpg',
    description: 'Versatile programming language for algorithms, data science, and web development',
    projects: ['Algorithm Solutions', 'Data Analysis Scripts', 'Automation Tools'],
    tools: ['PyCharm', 'Jupyter', 'pip', 'virtualenv']
  },

  // Database Technologies
  {
    name: 'MySQL',
    category: 'Database',
    experience: '5+ months',
    image: 'https://i.pinimg.com/736x/09/7b/34/097b349ab1d78c15744c3a89ff457939.jpg',
    description: 'Relational database management system',
    projects: ['School Database', 'E-commerce DB', 'User Management System'],
    tools: ['phpMyAdmin', 'MySQL Workbench', 'HeidiSQL', 'Sequel Pro']
  },

  // Styling Technologies
  {
    name: 'Tailwind CSS',
    category: 'Styling',
    experience: 'studying 1+ months',
    image: 'https://i.pinimg.com/736x/5e/42/c9/5e42c926feb229f934d3089d89c26e2f.jpg',
    description: 'Utility-first CSS framework for rapid UI development',
    projects: ['Modern Portfolio', 'Dashboard UI', 'Landing Pages'],
    tools: ['Tailwind CLI', 'Headless UI', 'Tailwind Play', 'VS Code Extension']
  },
  {
    name: 'Bootstrap 5',
    category: 'Styling',
    experience: '1+ years',
    image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/Bootstrap_logo.svg/800px-Bootstrap_logo.svg.png',
    description: 'Popular CSS framework for responsive web development',
    projects: ['Early Projects', 'Admin Dashboards', 'Business Websites'],
    tools: ['Bootstrap CDN', 'Bootstrap Studio', 'Sass', 'jQuery']
  },
  {
    name: 'Sass',
    category: 'Styling',
    experience: '1+ years',
    image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/Sass_Logo_Color.svg/1200px-Sass_Logo_Color.svg.png',
    description: 'CSS preprocessor with variables, nesting, and mixins',
    projects: ['Custom Themes', 'Component Libraries', 'Design Systems'],
    tools: ['VS Code', 'Sass CLI', 'Webpack', 'Gulp']
  },

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

const toolCategories = ['All', 'Code Editors', 'Design Tools', 'Learning Platforms', 'Development Tools', 'Project Management']

const tools = [
  // Code Editors
  {
    name: 'Visual Studio Code',
    category: 'Code Editors',
    icon: 'VS',
    image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Visual_Studio_Code_1.35_icon.svg/1200px-Visual_Studio_Code_1.35_icon.svg.png',
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
    image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/3/33/Figma-logo.svg/1200px-Figma-logo.svg.png',
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
    image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/a/a5/Google_Chrome_icon_%28September_2014%29.svg/1200px-Google_Chrome_icon_%28September_2014%29.svg.png',
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
    image: 'https://upload.wikimedia.org/wikipedia/en/thumb/7/78/XAMPP_logo.svg/1200px-XAMPP_logo.svg.png',
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
    image: 'https://yt3.googleusercontent.com/XRzDTgEa9GybH_Uk21E9ri6_iYh-9gbyZzhiEBCnLjISgjTorjMiu7IwpChUMf2lLpEdX6ufDA=s900-c-k-c0x00ffffff-no-rj',
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
    image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/0/09/YouTube_full-color_icon_%282017%29.svg/1200px-YouTube_full-color_icon_%282017%29.svg.png',
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
  
 
  // Project Management
  {
    name: 'Jira',
    category: 'Project Management',
    icon: 'J',
    image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/8/8a/Jira_Logo.svg/640px-Jira_Logo.svg.png',
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
    image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/e/e9/Notion-logo.svg/1200px-Notion-logo.svg.png',
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
  },
  // add git and github
  {
    name: 'Git & GitHub',
    category: 'Development Tools',
    icon: 'G',
    image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/9/91/Octicons-mark-github.svg/1200px-Octicons-mark-github.svg.png',
    usage: 'Daily Use',
    description: 'Version control system and code collaboration platform',
    detailedDescription: 'Git is used for version control, while GitHub provides a platform for hosting repositories, collaborating on code, and managing projects.',
    whyUse: 'Essential for version control, collaboration, and open source contributions. GitHub enhances Git with social features and project management tools.',
    features: [
      'Version control with Git',
      'Pull requests and code reviews',
      'Issue tracking',
      'Project boards',
      'Actions for CI/CD',
      'GitHub Pages for hosting'
    ],
    resources: [
      'Git Documentation',
      'GitHub Guides',
      'Pro Git Book',
      'GitHub Learning Lab'
    ]
  },
  // add thunder client
  {
    name: 'Thunder Client',
    category: 'Development Tools',
    icon: 'T',
    image: 'https://avatars.githubusercontent.com/u/164544218?s=200&v=4',
    usage: 'API Testing',
    description: 'Lightweight REST API client for testing APIs directly in VS Code',
    detailedDescription: 'Thunder Client is a fast and simple API client that integrates with VS Code, allowing quick API testing without leaving the editor.',
    whyUse: 'Lightweight, fast, and integrates seamlessly with VS Code. Perfect for quick API tests during development.',
    features: [
      'REST API testing',
      'Environment variables',
      'Collections for organizing requests',
      'Response history',
      'Code generation for requests',
      'VS Code integration'
    ],
    resources: [
      'Thunder Client Documentation',
      'Getting Started Guide',
      'API Testing Best Practices',
      'Community Resources'
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

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<style scoped>
.skill-icon-container,
.tool-icon-container {
  transition: all 0.3s ease;
}

.skill-image,
.tool-image {
  transition: all 0.3s ease;
}

.group:hover .skill-icon-container,
.group:hover .tool-icon-container {
  transform: scale(1.1);
}
</style>