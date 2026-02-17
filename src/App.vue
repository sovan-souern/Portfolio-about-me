<template>
  <div id="app" class="bg-white text-gray-900 min-h-screen">
    <!-- Navigation -->
    <Navbar />

    <!-- Main Content -->
    <main class="pt-20">
      <HomeView />
    </main>

    <!-- Footer -->
    <Footer />
    
    <!-- QR Code Floating Button -->
    <QRCodeFloating />
  </div>
</template>

<script setup>
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'
import HomeView from './views/HomeView.vue'
import QRCodeFloating from './components/QRCodeFloating.vue' // Import QR component
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
</style>