<template>
  <section class="relative z-10 py-20 bg-white">
    <div class="container mx-auto">
      <div class="text-center mb-8">
        <p class="section-subtitle">Taking Rides to a Next Level</p>
        <h2 class="section-title">Our Models</h2>
      </div>

      <!-- Capsule Tabs -->
      <div class="mb-12">
        <div class="flex flex-wrap justify-center gap-3">
          <button 
            v-for="tab in tabs" 
            :key="tab.id"
            @click="activeTab = tab.id; currentSlide = 0"
            class="px-6 py-2.5 rounded-full font-medium transition-all duration-300 text-sm border border-gray-200"
            :class="activeTab === tab.id 
              ? 'bg-dark text-white border-dark' 
              : 'bg-white text-dark hover:bg-dark hover:text-white hover:border-dark'"
          >
            {{ tab.name }}
          </button>
        </div>
      </div>

      <!-- Tab Content - Auto Carousel -->
      <div 
        class="relative" 
        @mouseenter="pauseAutoSlide" 
        @mouseleave="resumeAutoSlide"
      >
        <button 
          @click="manualPrevSlide"
          class="absolute left-0 top-1/2 -translate-y-1/2 -translate-x-4 z-10 w-10 h-10 bg-white shadow-lg rounded-full flex items-center justify-center hover:bg-dark hover:text-white transition-all duration-300"
          :class="{ 'opacity-0 pointer-events-none': currentSlide === 0 }"
          :disabled="currentSlide === 0"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
          </svg>
        </button>
        
        <button 
          @click="manualNextSlide"
          class="absolute right-0 top-1/2 -translate-y-1/2 translate-x-4 z-10 w-10 h-10 bg-white shadow-lg rounded-full flex items-center justify-center hover:bg-dark hover:text-white transition-all duration-300"
          :class="{ 'opacity-0 pointer-events-none': currentSlide >= maxSlides }"
          :disabled="currentSlide >= maxSlides"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
          </svg>
        </button>

        <div class="overflow-hidden px-2">
          <div 
            class="flex transition-transform duration-500 ease-out"
            :style="{ transform: `translateX(-${currentSlide * (100 / slidesPerView)}%)` }"
          >
            <div 
              v-for="car in filteredCars" 
              :key="car.id"
              class="flex-shrink-0 px-3"
              :style="{ width: `${100 / slidesPerView}%` }"
            >
              <div class="relative group text-center">
                <div class="relative overflow-hidden mb-4">
                  <img 
                    :src="car.image" 
                    :alt="car.name"
                    class="w-full h-auto object-contain group-hover:scale-105 transition-transform duration-500"
                  />
                  
                  <div class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300">
                    <NuxtLink 
                      :to="`/book-test-drive?car=${car.id}`" 
                      class="bg-primary text-white px-6 py-3 rounded-full font-semibold text-sm uppercase tracking-wider hover:bg-dark transition-all duration-300"
                    >
                      Book a Test Drive
                    </NuxtLink>
                  </div>
                </div>
                
                <h3 class="text-xl font-bold mb-3 text-dark">{{ car.name }}</h3>
                
                <NuxtLink 
                  :to="`/car/${car.id}`" 
                  class="text-primary font-medium hover:text-dark transition-colors inline-flex items-center gap-1"
                >
                  Learn More
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                  </svg>
                </NuxtLink>
              </div>
            </div>
          </div>
        </div>
        
        <div class="flex justify-center gap-2 mt-8">
          <button 
            v-for="(_, index) in Math.ceil(filteredCars.length / slidesPerView)" 
            :key="index"
            @click="goToSlide(index)"
            class="w-2 h-2 rounded-full transition-all duration-300"
            :class="currentSlide === index ? 'bg-primary w-6' : 'bg-gray-300 hover:bg-gray-400'"
          ></button>
        </div>
      </div>
      
      <div class="text-center mt-10">
        <NuxtLink 
          to="/stock" 
          class="inline-flex items-center gap-2 text-primary font-semibold hover:text-dark transition-colors"
        >
          View All Listings
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
          </svg>
        </NuxtLink>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted, watch } from 'vue'

const tabs = [
  { id: 'sedans', name: 'Sedans' },
  { id: 'suvs', name: 'SUVs & Crossovers' },
  { id: 'coupes', name: 'Coupés' },
  { id: 'cabriolets', name: 'Cabriolets' },
  { id: 'hatchbacks', name: 'Hatchbacks' },
  { id: 'mpv', name: 'MPV' },
  { id: 'estates', name: 'Estates' }
]

const activeTab = ref('suvs')
const currentSlide = ref(0)
const slidesPerView = ref(3)
let autoSlideInterval = null
const autoSlideDelay = 4000

const cars = ref([
  { id: 1, name: 'Toyota Corolla Cross', type: 'suvs', image: 'https://images.unsplash.com/photo-1581540222194-0d38b4d8a7d0?q=80&w=800&auto=format&fit=crop' },
  { id: 2, name: 'Toyota Axio Hybrid', type: 'sedans', image: 'https://images.unsplash.com/photo-1621007947382-bb3c3994e3fb?q=80&w=800&auto=format&fit=crop' },
  { id: 3, name: 'Toyota Fielder Hybrid', type: 'estates', image: 'https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?q=80&w=800&auto=format&fit=crop' },
  { id: 4, name: 'Toyota Noah', type: 'mpv', image: 'https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=800&auto=format&fit=crop' },
  { id: 5, name: 'Toyota Voxy', type: 'mpv', image: 'https://images.unsplash.com/photo-1549317661-bd32c8ce0db2?q=80&w=800&auto=format&fit=crop' },
  { id: 6, name: 'Honda Vezel Hybrid', type: 'suvs', image: 'https://images.unsplash.com/photo-1568605117036-5fe5e4ba0f5a?q=80&w=800&auto=format&fit=crop' },
  { id: 7, name: 'Toyota Harrier', type: 'suvs', image: 'https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?q=80&w=800&auto=format&fit=crop' },
  { id: 8, name: 'Honda Grace Hybrid', type: 'sedans', image: 'https://images.unsplash.com/photo-1621007947382-bb3c3994e3fb?q=80&w=800&auto=format&fit=crop' }
])

const filteredCars = computed(() => cars.value.filter(car => car.type === activeTab.value))
const maxSlides = computed(() => Math.max(0, Math.ceil(filteredCars.value.length / slidesPerView.value) - 1))

const startAutoSlide = () => {
  if (autoSlideInterval) clearInterval(autoSlideInterval)
  autoSlideInterval = setInterval(() => {
    if (currentSlide.value < maxSlides.value) currentSlide.value++
    else currentSlide.value = 0
  }, autoSlideDelay)
}

const pauseAutoSlide = () => {
  if (autoSlideInterval) {
    clearInterval(autoSlideInterval)
    autoSlideInterval = null
  }
}

const resumeAutoSlide = () => {
  if (filteredCars.value.length > slidesPerView.value) startAutoSlide()
}

const goToSlide = (index) => {
  currentSlide.value = index
  pauseAutoSlide()
  resumeAutoSlide()
}

const manualPrevSlide = () => {
  if (currentSlide.value > 0) {
    currentSlide.value--
    pauseAutoSlide()
    resumeAutoSlide()
  }
}

const manualNextSlide = () => {
  if (currentSlide.value < maxSlides.value) {
    currentSlide.value++
    pauseAutoSlide()
    resumeAutoSlide()
  }
}

const updateSlidesPerView = () => {
  if (typeof window !== 'undefined') {
    if (window.innerWidth < 640) slidesPerView.value = 1
    else if (window.innerWidth < 1024) slidesPerView.value = 2
    else slidesPerView.value = 3
  }
}

watch(activeTab, () => {
  currentSlide.value = 0
  pauseAutoSlide()
  setTimeout(() => { if (filteredCars.value.length > slidesPerView.value) startAutoSlide() }, 100)
})

watch(filteredCars, (newCars) => {
  pauseAutoSlide()
  if (newCars.length > slidesPerView.value) setTimeout(() => startAutoSlide(), 100)
})

onMounted(() => {
  updateSlidesPerView()
  window.addEventListener('resize', updateSlidesPerView)
  if (filteredCars.value.length > slidesPerView.value) startAutoSlide()
})

onUnmounted(() => {
  window.removeEventListener('resize', updateSlidesPerView)
  pauseAutoSlide()
})
</script>