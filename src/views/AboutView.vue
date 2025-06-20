<template>
  <div class="about-view py-20">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-20">
        <h1 class="text-5xl md:text-6xl font-bold mb-6">About Me</h1>
        <div class="w-24 h-1 bg-gradient-to-r from-blue-400 to-purple-600 mx-auto mb-8"></div>
        <p class="text-xl text-gray-400 max-w-3xl mx-auto">
          Passionate developer with a mission to create exceptional digital experiences
        </p>
      </div>

      <div class="grid lg:grid-cols-2 gap-16 items-center">
        <div>
          <img 
            src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?w=600&h=500&fit=crop" 
            alt="About Me" 
            class="rounded-2xl shadow-2xl"
          >
        </div>
        <div>
          <h2 class="text-3xl font-bold mb-6 text-blue-400">My Journey</h2>
          <p class="text-gray-300 mb-6 leading-relaxed">
            With over 5 years of experience in web development, I've had the privilege of working 
            with diverse clients and projects that have shaped my expertise in creating innovative 
            digital solutions.
          </p>
          <p class="text-gray-300 mb-6 leading-relaxed">
            My passion lies in transforming complex problems into elegant, user-friendly solutions. 
            I specialize in modern JavaScript frameworks, responsive design, and creating seamless 
            user experiences that drive business growth.
          </p>
          
          <div class="grid grid-cols-2 gap-6">
            <div class="bg-gray-900 p-4 rounded-lg">
              <h4 class="font-semibold text-blue-400 mb-2">Location</h4>
              <p class="text-gray-300">San Francisco, CA</p>
            </div>
            <div class="bg-gray-900 p-4 rounded-lg">
              <h4 class="font-semibold text-blue-400 mb-2">Experience</h4>
              <p class="text-gray-300">5+ Years</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>