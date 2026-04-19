<template>
  <section class="relative z-10 py-20 bg-gray-50">
    <div class="container mx-auto">
      <div class="text-center mb-12">
        <p class="section-subtitle">Real Deliveries, Real Customers</p>
        <h2 class="section-title">Social Proof</h2>
        <p class="text-gray-600 max-w-2xl mx-auto">See what our customers say about their CarBDShop experience.</p>
      </div>
      
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
        <div 
          v-for="(item, index) in galleryItems" 
          :key="index" 
          class="relative group overflow-hidden cursor-pointer"
          @click="openLightbox(item, index)"
        >
          <!-- Image for Delivery Photo and Happy Customer -->
          <img 
            v-if="item.type === 'image'"
            :src="item.image" 
            :alt="item.label" 
            @error="handleImageError"
            class="w-full h-48 object-cover group-hover:scale-105 transition-transform duration-500" 
          />
          
          <!-- Video Thumbnail for Inspection Video and Showroom -->
          <div v-else-if="item.type === 'video'" class="relative w-full h-48">
            <video 
              :src="item.video"
              muted
              loop
              playsinline
              class="w-full h-48 object-cover group-hover:scale-105 transition-transform duration-500"
              @mouseenter="playVideo"
              @mouseleave="pauseVideo"
              ref="videoRefs"
            ></video>
            <!-- Play Icon Overlay -->
            <div class="absolute inset-0 flex items-center justify-center bg-dark/20 group-hover:bg-dark/40 transition-all duration-300">
              <div class="w-12 h-12 bg-primary rounded-full flex items-center justify-center group-hover:scale-110 transition-transform duration-300">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-white" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M8 5v14l11-7z"/>
                </svg>
              </div>
            </div>
          </div>
          
          <!-- Hover Overlay -->
          <div class="absolute inset-0 bg-dark/50 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center pointer-events-none">
            <span class="text-white font-medium">{{ item.label }}</span>
            <span v-if="item.type === 'video'" class="absolute bottom-3 right-3 text-white/80 text-xs bg-dark/50 px-2 py-1 rounded">
              ▶ Video
            </span>
          </div>
        </div>
      </div>

      <!-- View More Link -->
      <div class="text-center mt-10">
        <NuxtLink 
          to="/gallery" 
          class="inline-flex items-center gap-2 text-primary font-semibold hover:text-dark transition-colors"
        >
          View Full Gallery
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
          </svg>
        </NuxtLink>
      </div>
    </div>

    <!-- Lightbox Modal -->
    <Teleport to="body">
      <div 
        v-if="lightboxOpen" 
        class="fixed inset-0 z-50 flex items-center justify-center bg-black/90"
        @click="closeLightbox"
      >
        <button 
          @click="closeLightbox"
          class="absolute top-5 right-5 text-white hover:text-primary transition-colors z-10"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
        
        <!-- Previous Button -->
        <button 
          v-if="galleryItems.length > 1"
          @click.stop="prevItem"
          class="absolute left-5 text-white hover:text-primary transition-colors"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
          </svg>
        </button>
        
        <!-- Next Button -->
        <button 
          v-if="galleryItems.length > 1"
          @click.stop="nextItem"
          class="absolute right-5 text-white hover:text-primary transition-colors"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
          </svg>
        </button>

        <div class="max-w-5xl max-h-[90vh] p-4" @click.stop>
          <!-- Lightbox Image -->
          <img 
            v-if="currentItem?.type === 'image'"
            :src="currentItem?.image" 
            :alt="currentItem?.label"
            class="max-w-full max-h-[85vh] object-contain"
          />
          
          <!-- Lightbox Video -->
          <video 
            v-else-if="currentItem?.type === 'video'"
            :src="currentItem?.video"
            controls
            autoplay
            class="max-w-full max-h-[85vh]"
          ></video>
          
          <p class="text-white text-center mt-4 text-lg">{{ currentItem?.label }}</p>
        </div>
      </div>
    </Teleport>
  </section>
</template>

<script setup>
import { ref } from 'vue'

// Default fallback image
const DEFAULT_IMAGE = 'https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=400&auto=format&fit=crop'

const galleryItems = ref([
  { 
    type: 'image',
    image: 'https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=400&auto=format&fit=crop', 
    label: 'Delivery Photo' 
  },
  { 
    type: 'video',
    video: '/video/showroom.mp4',
    image: DEFAULT_IMAGE,
    label: 'Inspection Video' 
  },
  {
    type: 'image',
    image: 'https://images.unsplash.com/photo-1549317661-bd32c8ce0db2?q=80&w=400&auto=format&fit=crop',
    label: 'New Arrival'
  },
  { 
    type: 'video',
    video: '/video/showroom.mp4',
    image: DEFAULT_IMAGE,
    label: 'Showroom' 
  }
  
])

// Video refs for hover play
const videoRefs = ref([])

// Lightbox state
const lightboxOpen = ref(false)
const currentIndex = ref(0)
const currentItem = ref(null)

// Play video on hover
const playVideo = (event) => {
  const video = event.target.querySelector('video') || event.target
  if (video && video.play) {
    video.play().catch(() => {})
  }
}

// Pause video on hover leave
const pauseVideo = (event) => {
  const video = event.target.querySelector('video') || event.target
  if (video && video.pause) {
    video.pause()
    video.currentTime = 0
  }
}

// Handle image error
const handleImageError = (event) => {
  event.target.src = DEFAULT_IMAGE
}

// Open lightbox
const openLightbox = (item, index) => {
  currentItem.value = item
  currentIndex.value = index
  lightboxOpen.value = true
  document.body.style.overflow = 'hidden'
}

// Close lightbox
const closeLightbox = () => {
  lightboxOpen.value = false
  document.body.style.overflow = ''
}

// Previous item
const prevItem = () => {
  currentIndex.value = currentIndex.value > 0 
    ? currentIndex.value - 1 
    : galleryItems.value.length - 1
  currentItem.value = galleryItems.value[currentIndex.value]
}

// Next item
const nextItem = () => {
  currentIndex.value = currentIndex.value < galleryItems.value.length - 1 
    ? currentIndex.value + 1 
    : 0
  currentItem.value = galleryItems.value[currentIndex.value]
}

// Keyboard navigation
if (typeof window !== 'undefined') {
  window.addEventListener('keydown', (e) => {
    if (!lightboxOpen.value) return
    if (e.key === 'Escape') closeLightbox()
    if (e.key === 'ArrowLeft') prevItem()
    if (e.key === 'ArrowRight') nextItem()
  })
}
</script>