<template>
  <!-- Footer -->
  <footer class="bg-gray-900 text-white py-12">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="flex flex-col md:flex-row justify-between items-center">
              <div class="mb-6 md:mb-0">
                  <h2 class="text-2xl font-bold">Albert Garcia</h2>
                  <p class="text-gray-400 mt-2">Web Developer</p>
              </div>
              <div class="flex space-x-6">
                  <a v-for="social in socialLinks" :key="social.icon" href="#" class="text-gray-400 hover:text-white transition">
                      <i :class="`fab fa-${social.icon} text-xl`"></i>
                  </a>
              </div>
          </div>
          <div class="border-t border-gray-800 mt-8 pt-8 flex flex-col md:flex-row justify-between items-center">
              <p class="text-gray-400 text-sm mb-4 md:mb-0">© 2023 Albert Garcia. All rights reserved.</p>
              <div class="flex space-x-6">
                  <a href="#" class="text-gray-400 hover:text-white text-sm transition">Privacy Policy</a>
                  <a href="#" class="text-gray-400 hover:text-white text-sm transition">Terms of Service</a>
              </div>
          </div>
      </div>
  </footer>
</template>

<script setup>
  const socialLinks = [
    { icon: 'facebook-f' },
    { icon: 'twitter' },
    { icon: 'linkedin-in' },
    { icon: 'github' }
  ]
</script>

<style scoped lang="sass">
  
</style>
