<template>
  <header class="text-white z-50" :class="isHomePage ? 'bg-transparent' : 'bg-dark'">
    <!-- Top Bar - Logo Left, Login/Signup Right -->
    <div class="container mx-auto">
      <div class="flex justify-between items-center py-4">
        <!-- Logo - Left (50% larger) -->
        <NuxtLink to="/" class="flex items-center">
          <img 
            src="/images/logo.png" 
            alt="CarBDShop" 
            class="h-14 md:h-16 lg:h-20 w-auto"
          />
        </NuxtLink>
        
        <!-- Login/Signup - Right -->
        <div class="flex items-center gap-2 text-sm">
          <NuxtLink to="/login" class="hover:text-primary transition-colors">Login</NuxtLink>
          <span class="text-white/30">/</span>
          <NuxtLink to="/signup" class="hover:text-primary transition-colors">Sign Up</NuxtLink>
        </div>
      </div>
    </div>
    
    <!-- Main Header - Navigation Bar -->
    <div class="border-t border-white/10">
      <div class="container mx-auto">
        <div class="flex items-center justify-between py-3">
          <!-- Desktop Navigation - Left aligned -->
          <nav class="hidden lg:flex items-center gap-8">
            <NuxtLink to="/" class="text-white hover:text-primary transition-colors font-medium text-sm uppercase tracking-wider">
              Home
            </NuxtLink>
            <NuxtLink to="/stock" class="text-white hover:text-primary transition-colors font-medium text-sm uppercase tracking-wider">
              Stock
            </NuxtLink>
            <NuxtLink to="/prebook" class="text-white hover:text-primary transition-colors font-medium text-sm uppercase tracking-wider">
              Prebook
            </NuxtLink>
            <NuxtLink to="/import-process" class="text-white hover:text-primary transition-colors font-medium text-sm uppercase tracking-wider">
              Import Process
            </NuxtLink>
            <NuxtLink to="/finance" class="text-white hover:text-primary transition-colors font-medium text-sm uppercase tracking-wider">
              Finance
            </NuxtLink>
            <NuxtLink to="/blog" class="text-white hover:text-primary transition-colors font-medium text-sm uppercase tracking-wider">
              Blog
            </NuxtLink>
            <NuxtLink to="/contact" class="text-white hover:text-primary transition-colors font-medium text-sm uppercase tracking-wider">
              Contact
            </NuxtLink>
          </nav>
          
          <!-- Right Actions - Phone and Mobile Menu -->
          <div class="flex items-center gap-4">
            <a 
              href="tel:+8801987576688" 
              class="hidden md:flex items-center gap-2 text-white hover:text-primary transition-colors"
            >
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
              </svg>
              <span>+880 1987576688</span>
            </a>
            <a 
              href="tel:+8801939901253" 
              class="hidden md:flex items-center gap-2 text-white hover:text-primary transition-colors"
            >
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
              </svg>
              <span>+880 1939901253</span>
            </a>
            
            <!-- Mobile Menu Button -->
            <button 
              @click="mobileMenuOpen = !mobileMenuOpen" 
              class="lg:hidden text-white hover:text-primary transition-colors"
              aria-label="Toggle menu"
            >
              <svg v-if="!mobileMenuOpen" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
              </svg>
              <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
              </svg>
            </button>
          </div>
        </div>
      </div>
    </div>
    
    <!-- Mobile Menu -->
    <Transition name="slide-down">
      <div v-if="mobileMenuOpen" class="lg:hidden bg-dark border-t border-white/10">
        <div class="container mx-auto py-4 flex flex-col gap-1">
          <NuxtLink 
            to="/" 
            class="text-white hover:text-primary hover:bg-white/5 transition-all duration-300 py-3 px-4 rounded-lg font-medium text-sm uppercase tracking-wider"
            @click="mobileMenuOpen = false"
          >
            Home
          </NuxtLink>
          <NuxtLink 
            to="/stock" 
            class="text-white hover:text-primary hover:bg-white/5 transition-all duration-300 py-3 px-4 rounded-lg font-medium text-sm uppercase tracking-wider"
            @click="mobileMenuOpen = false"
          >
            Stock
          </NuxtLink>
          <NuxtLink 
            to="/prebook" 
            class="text-white hover:text-primary hover:bg-white/5 transition-all duration-300 py-3 px-4 rounded-lg font-medium text-sm uppercase tracking-wider"
            @click="mobileMenuOpen = false"
          >
            Prebook
          </NuxtLink>
          <NuxtLink 
            to="/import-process" 
            class="text-white hover:text-primary hover:bg-white/5 transition-all duration-300 py-3 px-4 rounded-lg font-medium text-sm uppercase tracking-wider"
            @click="mobileMenuOpen = false"
          >
            Import Process
          </NuxtLink>
          <NuxtLink 
            to="/finance" 
            class="text-white hover:text-primary hover:bg-white/5 transition-all duration-300 py-3 px-4 rounded-lg font-medium text-sm uppercase tracking-wider"
            @click="mobileMenuOpen = false"
          >
            Finance
          </NuxtLink>
          <NuxtLink 
            to="/blog" 
            class="text-white hover:text-primary hover:bg-white/5 transition-all duration-300 py-3 px-4 rounded-lg font-medium text-sm uppercase tracking-wider"
            @click="mobileMenuOpen = false"
          >
            Blog
          </NuxtLink>
          <NuxtLink 
            to="/contact" 
            class="text-white hover:text-primary hover:bg-white/5 transition-all duration-300 py-3 px-4 rounded-lg font-medium text-sm uppercase tracking-wider"
            @click="mobileMenuOpen = false"
          >
            Contact
          </NuxtLink>
          
          <!-- Mobile Login/Signup -->
          <div class="flex gap-4 pt-4 mt-2 border-t border-white/10">
            <NuxtLink 
              to="/login" 
              class="flex-1 text-center text-white border border-white/30 hover:border-primary hover:bg-primary transition-all duration-300 py-3 px-4 rounded-lg font-medium"
              @click="mobileMenuOpen = false"
            >
              Login
            </NuxtLink>
            <NuxtLink 
              to="/signup" 
              class="flex-1 text-center bg-primary text-white hover:bg-white hover:text-dark transition-all duration-300 py-3 px-4 rounded-lg font-medium"
              @click="mobileMenuOpen = false"
            >
              Sign Up
            </NuxtLink>
          </div>
        </div>
      </div>
    </Transition>
  </header>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const mobileMenuOpen = ref(false)

// Check if current page is homepage
const isHomePage = computed(() => route.path === '/')

// Close mobile menu on window resize if screen becomes large
const handleResize = () => {
  if (window.innerWidth >= 1024) {
    mobileMenuOpen.value = false
  }
}

onMounted(() => {
  window.addEventListener('resize', handleResize)
})

onUnmounted(() => {
  window.removeEventListener('resize', handleResize)
})
</script>

<style scoped>
.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.3s ease;
}

.slide-down-enter-from,
.slide-down-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>