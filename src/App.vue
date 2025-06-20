<template>
  <nav class="bg-gray-800">
    <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
      <div class="relative flex h-16 items-center justify-between">
        <!-- Logo -->
        <div class="flex flex-1 items-center justify-start">
          <RouterLink to="/" class="flex items-center">
            <span class="text-white text-lg font-bold ml-2">My App</span>
          </RouterLink>
        </div>

        <!-- Desktop Menu -->
        <div class="hidden sm:ml-6 sm:block">
          <div class="flex space-x-4">
            <RouterLink
              to="/"
              class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium"
              active-class="bg-gray-900 text-white"
              exact
            >Home</RouterLink>

            <RouterLink
              to="/about"
              class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium"
              active-class="bg-gray-900 text-white"
            >About</RouterLink>

            <RouterLink
              to="/service"
              class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium"
              active-class="bg-gray-900 text-white"
            >Service</RouterLink>
            <RouterLink
              to="/portfolio"
              class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium"
              active-class="bg-gray-900 text-white"
            >Portfolio</RouterLink>
            <RouterLink
              to="/contact"
              class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium"
              active-class="bg-gray-900 text-white"
            >Contact</RouterLink>
          </div>
        </div>
      </div>
    </div>
  </nav>

  <!-- Main Page Content -->
  <RouterView />
</template>

<style scoped>
/* Optional: to handle focus rings nicely */
:focus {
  outline: none;
}
</style>
