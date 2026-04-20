<template>
  <div>
    <!-- Hero Section with Car Image Background -->
    <section class="relative min-h-screen flex items-center z-10">
      <!-- Car Image Background -->
      <div class="absolute inset-0 z-0">
        <img 
          :src="car?.image || DEFAULT_CAR_IMAGE" 
          :alt="car?.name"
          class="w-full h-full object-cover"
          @error="handleImageError"
        />
        <!-- Dark gradient overlay -->
        <div class="absolute inset-0 bg-gradient-to-r from-black/80 via-black/50 to-transparent"></div>
      </div>

      <!-- Hero Content -->
      <div class="container mx-auto relative z-10 py-20">
        <div class="max-w-4xl">
          <!-- Model Badge -->
          <div class="mb-8 flex items-center gap-3">
            <span class="text-white text-sm font-light tracking-[0.3em] uppercase">{{ car?.category || 'Premium' }}</span>
            <span class="w-12 h-[1px] bg-primary"></span>
            <span class="text-white text-sm font-light tracking-[0.3em] uppercase">Japanese Import</span>
          </div>
          
          <!-- Model Name -->
          <h1 class="text-5xl md:text-7xl lg:text-8xl font-bold text-white mb-6 leading-[1.1]">
            {{ car?.name || 'Model' }}
          </h1>
          
          <!-- Supporting Text -->
          <p class="text-lg md:text-xl text-white/80 mb-10 max-w-xl leading-relaxed">
            {{ car?.description || 'Premium Japanese vehicle, fully inspected and verified for quality.' }}
          </p>
          
          <!-- CTA Buttons -->
          <div class="flex flex-wrap gap-4">
            <NuxtLink 
              :to="`/book-test-drive?car=${car?.id}`"
              class="group relative inline-flex items-center gap-3 bg-primary text-white px-8 py-4 font-semibold text-sm uppercase tracking-wider hover:bg-white hover:text-dark transition-all duration-300"
            >
              <span>Book a Test Drive</span>
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 group-hover:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
              </svg>
            </NuxtLink>
            
            <a 
              :href="`https://wa.me/8801987576688?text=I'm interested in the ${car?.name}`"
              target="_blank" 
              class="group inline-flex items-center gap-3 border border-white/30 text-white px-8 py-4 font-semibold text-sm uppercase tracking-wider hover:border-primary hover:bg-primary transition-all duration-300"
            >
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
                <path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.582 2.128 2.182-.573c.978.58 1.911.928 3.145.929 3.178 0 5.767-2.587 5.768-5.766.001-3.187-2.575-5.77-5.764-5.771z"/>
              </svg>
              <span>WhatsApp Inquiry</span>
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 group-hover:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
              </svg>
            </a>
            
            <NuxtLink 
              to="/prebook" 
              class="group inline-flex items-center gap-3 border border-white/30 text-white px-8 py-4 font-semibold text-sm uppercase tracking-wider hover:border-primary hover:bg-primary transition-all duration-300"
            >
              <span>Prebook This Car</span>
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 group-hover:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
              </svg>
            </NuxtLink>
          </div>
        </div>
      </div>
      
      <!-- Scroll Indicator -->
      <div class="absolute bottom-8 left-1/2 -translate-x-1/2 z-10 hidden md:block">
        <div class="flex flex-col items-center gap-2 text-white/50">
          <span class="text-xs uppercase tracking-widest">Scroll</span>
          <div class="w-[1px] h-16 bg-gradient-to-b from-white/50 to-transparent"></div>
        </div>
      </div>
    </section>

    <!-- Sticky Navigation Bar -->
    <div class="sticky top-0 z-40 bg-dark border-b border-white/10">
      <div class="container mx-auto">
        <div class="flex items-center justify-between py-4">
          <span class="text-white font-bold text-lg">{{ car?.name }}</span>
          <div class="hidden md:flex gap-6">
            <a href="#overview" class="text-white/70 hover:text-primary text-sm uppercase tracking-wider transition-colors">Overview</a>
            <a href="#specifications" class="text-white/70 hover:text-primary text-sm uppercase tracking-wider transition-colors">Specifications</a>
            <a href="#features" class="text-white/70 hover:text-primary text-sm uppercase tracking-wider transition-colors">Features</a>
            <a href="#gallery" class="text-white/70 hover:text-primary text-sm uppercase tracking-wider transition-colors">Gallery</a>
            <a href="#inquiry" class="text-white/70 hover:text-primary text-sm uppercase tracking-wider transition-colors">Inquiry</a>
          </div>
          <NuxtLink 
            :to="`/book-test-drive?car=${car?.id}`"
            class="bg-primary text-white px-4 py-2 text-sm uppercase tracking-wider hover:bg-primary/80 transition-all duration-300"
          >
            Book Test Drive
          </NuxtLink>
        </div>
      </div>
    </div>

    <!-- Overview Section -->
    <section id="overview" class="relative z-10 py-20 bg-white">
      <div class="container mx-auto">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
          <div>
            <p class="section-subtitle">Premium Japanese Import</p>
            <h2 class="section-title">{{ car?.name }}</h2>
            <p class="text-gray-600 mb-6 leading-relaxed">
              {{ car?.description || 'This exceptional vehicle represents the pinnacle of Japanese automotive engineering. Sourced directly from Japan auctions with full transparency and verified auction grades.' }}
            </p>
            
            <!-- Key Highlights -->
            <div class="grid grid-cols-2 gap-4 mt-8">
              <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
                <span class="text-dark font-medium">Auction Grade Verified</span>
              </div>
              <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
                <span class="text-dark font-medium">Full Inspection Report</span>
              </div>
              <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
                <span class="text-dark font-medium">Direct from Japan</span>
              </div>
              <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
                <span class="text-dark font-medium">BRTA Support</span>
              </div>
            </div>
          </div>
          
          <div class="relative">
            <img 
              :src="car?.image || DEFAULT_CAR_IMAGE" 
              :alt="car?.name"
              class="w-full h-auto shadow-2xl rounded-lg"
              @error="handleImageError"
            />
          </div>
        </div>
      </div>
    </section>

    <!-- Specifications Section -->
    <section id="specifications" class="relative z-10 py-20 bg-gray-50">
      <div class="container mx-auto">
        <div class="text-center mb-12">
          <p class="section-subtitle">Technical Details</p>
          <h2 class="section-title">Specifications</h2>
        </div>
        
        <div class="max-w-4xl mx-auto bg-white shadow-xl rounded-lg overflow-hidden">
          <div class="grid grid-cols-1 md:grid-cols-2 divide-y md:divide-y-0 md:divide-x divide-gray-200">
            <div class="p-8">
              <h3 class="text-lg font-bold mb-6 flex items-center gap-3">
                <span class="w-8 h-[2px] bg-primary"></span>
                Performance
              </h3>
              <dl class="space-y-4">
                <div class="flex justify-between">
                  <dt class="text-gray-600">Fuel Type</dt>
                  <dd class="font-semibold text-dark">{{ car?.fuelType || 'Hybrid' }}</dd>
                </div>
                <div class="flex justify-between">
                  <dt class="text-gray-600">Mileage</dt>
                  <dd class="font-semibold text-dark">{{ car?.mileage || '25 km/L' }}</dd>
                </div>
                <div class="flex justify-between">
                  <dt class="text-gray-600">Transmission</dt>
                  <dd class="font-semibold text-dark">{{ car?.transmission || 'CVT' }}</dd>
                </div>
                <div class="flex justify-between">
                  <dt class="text-gray-600">Drive Type</dt>
                  <dd class="font-semibold text-dark">{{ car?.driveType || '2WD' }}</dd>
                </div>
                <div class="flex justify-between">
                  <dt class="text-gray-600">Engine</dt>
                  <dd class="font-semibold text-dark">1.8L 4-Cylinder Hybrid</dd>
                </div>
              </dl>
            </div>
            <div class="p-8">
              <h3 class="text-lg font-bold mb-6 flex items-center gap-3">
                <span class="w-8 h-[2px] bg-primary"></span>
                Dimensions
              </h3>
              <dl class="space-y-4">
                <div class="flex justify-between">
                  <dt class="text-gray-600">Length</dt>
                  <dd class="font-semibold text-dark">4,630 mm</dd>
                </div>
                <div class="flex justify-between">
                  <dt class="text-gray-600">Width</dt>
                  <dd class="font-semibold text-dark">1,780 mm</dd>
                </div>
                <div class="flex justify-between">
                  <dt class="text-gray-600">Height</dt>
                  <dd class="font-semibold text-dark">1,435 mm</dd>
                </div>
                <div class="flex justify-between">
                  <dt class="text-gray-600">Wheelbase</dt>
                  <dd class="font-semibold text-dark">2,700 mm</dd>
                </div>
                <div class="flex justify-between">
                  <dt class="text-gray-600">Seating Capacity</dt>
                  <dd class="font-semibold text-dark">5 Persons</dd>
                </div>
              </dl>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Features Section -->
    <section id="features" class="relative z-10 py-20 bg-white">
      <div class="container mx-auto">
        <div class="text-center mb-12">
          <p class="section-subtitle">Highlights</p>
          <h2 class="section-title">Key Features</h2>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div v-for="(feature, index) in features" :key="index" class="bg-gray-50 p-6 rounded-lg hover:shadow-lg transition-all duration-300 border border-gray-100">
            <div class="w-12 h-12 bg-primary/10 rounded-full flex items-center justify-center mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
              </svg>
            </div>
            <h3 class="text-lg font-bold mb-2">{{ feature.title }}</h3>
            <p class="text-gray-600 text-sm">{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Gallery Section -->
    <section id="gallery" class="relative z-10 py-20 bg-gray-50">
      <div class="container mx-auto">
        <div class="text-center mb-12">
          <p class="section-subtitle">Visual Tour</p>
          <h2 class="section-title">Gallery</h2>
        </div>
        
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
          <div 
            v-for="(img, index) in galleryImages" 
            :key="index"
            class="relative group overflow-hidden rounded-lg cursor-pointer"
            @click="openLightbox(index)"
          >
            <img 
              :src="img" 
              :alt="`${car?.name} view ${index + 1}`"
              class="w-full h-48 object-cover group-hover:scale-105 transition-transform duration-500"
              @error="handleImageError"
            />
            <div class="absolute inset-0 bg-dark/50 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0zM10 7v6m4-3H8" />
              </svg>
            </div>
          </div>
        </div>
      </div>

      <!-- Lightbox -->
      <Teleport to="body">
        <div 
          v-if="lightboxOpen" 
          class="fixed inset-0 z-50 flex items-center justify-center bg-black/95"
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
          
          <button 
            v-if="galleryImages.length > 1"
            @click.stop="prevImage"
            class="absolute left-5 text-white hover:text-primary transition-colors"
          >
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
            </svg>
          </button>
          
          <button 
            v-if="galleryImages.length > 1"
            @click.stop="nextImage"
            class="absolute right-5 text-white hover:text-primary transition-colors"
          >
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
            </svg>
          </button>

          <div class="max-w-5xl max-h-[90vh] p-4" @click.stop>
            <img 
              :src="galleryImages[currentImageIndex]" 
              :alt="`${car?.name} view ${currentImageIndex + 1}`"
              class="max-w-full max-h-[85vh] object-contain"
            />
            <p class="text-white text-center mt-4">
              {{ currentImageIndex + 1 }} / {{ galleryImages.length }}
            </p>
          </div>
        </div>
      </Teleport>
    </section>

    <!-- Inquiry Form Section -->
    <section id="inquiry" class="relative z-10 py-20 bg-dark">
      <div class="container mx-auto">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
          <div>
            <p class="section-subtitle text-primary">Experience it on the road</p>
            <h2 class="section-title text-white">Test Drive the {{ car?.name }}</h2>
            <p class="text-white/70 mb-8 leading-relaxed">
              Send us a request to test drive the {{ car?.name }} and we will get back to you soon.
            </p>
            
            <div class="space-y-4 text-white/60">
              <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                </svg>
                <span>+880 1987576688</span>
              </div>
              <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 7.89a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                </svg>
                <span>sales@carbdshop.com</span>
              </div>
            </div>
          </div>
          
          <!-- Dark Themed Form -->
          <div class="bg-dark/40 backdrop-blur-sm border border-white/10 shadow-2xl p-8">
            <form @submit.prevent="handleInquirySubmit" class="space-y-6">
              <h3 class="text-xl font-bold text-white mb-4 flex items-center gap-3">
                <span class="w-8 h-[2px] bg-primary"></span>
                Request a Test Drive
              </h3>
              
              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <input 
                  type="text" 
                  v-model="inquiryForm.firstName"
                  required
                  placeholder="First Name *"
                  class="w-full px-4 py-3 bg-white/10 border border-white/20 focus:border-primary focus:outline-none text-white placeholder-white/40"
                />
                <input 
                  type="text" 
                  v-model="inquiryForm.lastName"
                  required
                  placeholder="Last Name *"
                  class="w-full px-4 py-3 bg-white/10 border border-white/20 focus:border-primary focus:outline-none text-white placeholder-white/40"
                />
              </div>
              
              <input 
                type="email" 
                v-model="inquiryForm.email"
                required
                placeholder="Email Address *"
                class="w-full px-4 py-3 bg-white/10 border border-white/20 focus:border-primary focus:outline-none text-white placeholder-white/40"
              />
              
              <input 
                type="tel" 
                v-model="inquiryForm.phone"
                required
                placeholder="Contact Number *"
                class="w-full px-4 py-3 bg-white/10 border border-white/20 focus:border-primary focus:outline-none text-white placeholder-white/40"
              />
              
              <textarea 
                v-model="inquiryForm.message"
                rows="4"
                placeholder="Message (Optional)"
                class="w-full px-4 py-3 bg-white/10 border border-white/20 focus:border-primary focus:outline-none text-white placeholder-white/40 resize-none"
              ></textarea>
              
              <!-- Preferred Contact Time -->
              <div>
                <label class="block text-xs font-semibold uppercase tracking-wider text-white/60 mb-2">Preferred Contact Time</label>
                <select 
                  v-model="inquiryForm.preferredTime"
                  class="w-full px-4 py-3 bg-white/10 border border-white/20 focus:border-primary focus:outline-none text-white"
                >
                  <option value="" class="text-dark">Select preferred time</option>
                  <option value="morning" class="text-dark">Morning (9AM - 12PM)</option>
                  <option value="afternoon" class="text-dark">Afternoon (12PM - 4PM)</option>
                  <option value="evening" class="text-dark">Evening (4PM - 8PM)</option>
                  <option value="anytime" class="text-dark">Anytime</option>
                </select>
              </div>
              
              <!-- Agreement -->
              <div class="flex items-center gap-3">
                <input 
                  type="checkbox" 
                  v-model="inquiryForm.agreement"
                  required
                  class="w-4 h-4 text-primary bg-white/10 border-white/20 focus:ring-primary"
                />
                <label class="text-sm text-white/70">
                  I agree to be contacted by CarBDShop regarding my test drive request.
                </label>
              </div>
              
              <button 
                type="submit"
                class="w-full bg-primary text-white px-6 py-4 font-semibold text-sm uppercase tracking-wider hover:bg-white hover:text-dark transition-all duration-300"
              >
                Submit Request
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 inline ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
                </svg>
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const DEFAULT_CAR_IMAGE = 'https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=1920&auto=format&fit=crop'

// Cars data (same as in OurModels.vue)
const cars = ref([
  // SUVs
  { id: 1, name: 'Toyota Corolla Cross', category: 'SUV', type: 'suvs', image: '/images/toyota-corolla-cross.jpg', fuelType: 'Hybrid', mileage: '25 km/L', transmission: 'CVT', driveType: '2WD', description: 'The Toyota Corolla Cross combines SUV versatility with hybrid efficiency. Perfect for Bangladeshi roads.' },
  { id: 2, name: 'Honda Vezel Hybrid', category: 'SUV', type: 'suvs', image: '/images/Honda-Vezel-Hybrid-RS-Honda-Sensing.jpg', fuelType: 'Hybrid', mileage: '24 km/L', transmission: 'CVT', driveType: '2WD', description: 'Stylish and efficient, the Honda Vezel Hybrid offers premium features with exceptional fuel economy.' },
  { id: 3, name: 'Toyota Harrier', category: 'SUV', type: 'suvs', image: '/images/Toyota Harrier.jpg', fuelType: 'Hybrid', mileage: '22 km/L', transmission: 'CVT', driveType: 'AWD', description: 'The premium Toyota Harrier delivers luxury SUV experience with advanced hybrid technology.' },
  
  // Sedans
  { id: 7, name: 'Toyota Axio Hybrid', category: 'Sedan', type: 'sedans', image: '/images/sedan-1.jpg', fuelType: 'Hybrid', mileage: '30 km/L', transmission: 'CVT', driveType: '2WD', description: 'The Toyota Axio Hybrid is the perfect family sedan with outstanding fuel efficiency and reliability.' },
  { id: 8, name: 'Honda Grace Hybrid', category: 'Sedan', type: 'sedans', image: '/images/sedan-2.jpg', fuelType: 'Hybrid', mileage: '28 km/L', transmission: 'CVT', driveType: '2WD', description: 'Elegant and efficient, the Honda Grace Hybrid offers a premium driving experience with hybrid economy.' },
  { id: 9, name: 'Toyota Camry', category: 'Sedan', type: 'sedans', image: '/images/sedan-3.jpg', fuelType: 'Hybrid', mileage: '20 km/L', transmission: 'CVT', driveType: '2WD', description: 'The legendary Toyota Camry delivers executive comfort with world-class reliability.' },
  
  // Coupés
  { id: 12, name: 'Toyota GR86', category: 'Coupé', type: 'coupes', image: '/images/coupes-1.webp', fuelType: 'Petrol', mileage: '12 km/L', transmission: 'Manual', driveType: 'RWD', description: 'Pure driving pleasure - the Toyota GR86 is a lightweight sports coupe designed for enthusiasts.' },
  { id: 13, name: 'Subaru BRZ', category: 'Coupé', type: 'coupes', image: '/images/coupes-2.jpg', fuelType: 'Petrol', mileage: '12 km/L', transmission: 'Manual', driveType: 'RWD', description: 'The Subaru BRZ offers razor-sharp handling and classic sports car proportions.' },
  
  // Cabriolets
  { id: 15, name: 'Mazda MX-5 RF', category: 'Cabriolet', type: 'cabriolets', image: '/images/cabriolets-1.webp', fuelType: 'Petrol', mileage: '14 km/L', transmission: 'Manual', driveType: 'RWD', description: 'The iconic Mazda MX-5 RF delivers open-top driving joy with retractable hardtop convenience.' },
  
  // Hatchbacks
  { id: 17, name: 'Toyota Yaris', category: 'Hatchback', type: 'hatchbacks', image: '/images/hatchbacks-1.jpg', fuelType: 'Petrol', mileage: '18 km/L', transmission: 'CVT', driveType: '2WD', description: 'Compact and nimble, the Toyota Yaris is perfect for city driving with excellent fuel economy.' },
  { id: 18, name: 'Honda Fit', category: 'Hatchback', type: 'hatchbacks', image: '/images/hatchbacks-2.webp', fuelType: 'Hybrid', mileage: '25 km/L', transmission: 'CVT', driveType: '2WD', description: 'The versatile Honda Fit offers surprising interior space in a compact package with hybrid efficiency.' },
  
  // MPV
  { id: 20, name: 'Toyota Noah', category: 'MPV', type: 'mpv', image: '/images/noah.jpg', fuelType: 'Hybrid', mileage: '22 km/L', transmission: 'CVT', driveType: '2WD', description: 'The Toyota Noah is the ultimate family vehicle with spacious 7-seater configuration and hybrid efficiency.' },
  { id: 21, name: 'Toyota Voxy', category: 'MPV', type: 'mpv', image: '/images/voxy.jpg', fuelType: 'Hybrid', mileage: '22 km/L', transmission: 'CVT', driveType: '2WD', description: 'Stylish and practical, the Toyota Voxy offers premium family transport with bold design.' },
  { id: 22, name: 'Honda StepWGN', category: 'MPV', type: 'mpv', image: '/images/stepwgn.jpg', fuelType: 'Hybrid', mileage: '20 km/L', transmission: 'CVT', driveType: '2WD', description: 'The innovative Honda StepWGN features a unique tailgate design and flexible interior configurations.' },
  
  // Estates
  { id: 24, name: 'Toyota Fielder Hybrid', category: 'Wagon', type: 'estates', image: '/images/estates-1.jpg', fuelType: 'Hybrid', mileage: '28 km/L', transmission: 'CVT', driveType: '2WD', description: 'The Toyota Fielder Hybrid combines wagon practicality with exceptional hybrid fuel economy.' },
  { id: 25, name: 'Subaru Levorg', category: 'Wagon', type: 'estates', image: '/images/estates-2.jpg', fuelType: 'Petrol', mileage: '14 km/L', transmission: 'CVT', driveType: 'AWD', description: 'The Subaru Levorg offers sports wagon styling with legendary Subaru AWD capability.' },
])

// Find current car based on ID
const car = computed(() => cars.value.find(c => c.id === parseInt(route.params.id)))

// Features list
const features = ref([
  { title: 'Advanced Safety', description: 'Multiple airbags, ABS, stability control, and advanced driver assistance systems.' },
  { title: 'Premium Audio', description: 'High-quality sound system with smartphone connectivity and navigation.' },
  { title: 'Comfort Features', description: 'Automatic climate control, power seats, and keyless entry with push-button start.' },
  { title: 'LED Lighting', description: 'Energy-efficient LED headlights, taillights, and daytime running lights.' },
  { title: 'Smart Entry', description: 'Keyless entry and push-button start for convenient access.' },
  { title: 'Cruise Control', description: 'Adaptive cruise control for relaxed highway driving.' },
])

// Gallery images (using car image + fallbacks)
const galleryImages = computed(() => {
  const images = [car.value?.image || DEFAULT_CAR_IMAGE]
  images.push('https://images.unsplash.com/photo-1581540222194-0d38b4d8a7d0?q=80&w=800&auto=format&fit=crop')
  images.push('https://images.unsplash.com/photo-1568605117036-5fe5e4ba0f5a?q=80&w=800&auto=format&fit=crop')
  images.push('https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?q=80&w=800&auto=format&fit=crop')
  return images
})

// Lightbox state
const lightboxOpen = ref(false)
const currentImageIndex = ref(0)

const openLightbox = (index) => {
  currentImageIndex.value = index
  lightboxOpen.value = true
  document.body.style.overflow = 'hidden'
}

const closeLightbox = () => {
  lightboxOpen.value = false
  document.body.style.overflow = ''
}

const prevImage = () => {
  currentImageIndex.value = currentImageIndex.value > 0 
    ? currentImageIndex.value - 1 
    : galleryImages.value.length - 1
}

const nextImage = () => {
  currentImageIndex.value = currentImageIndex.value < galleryImages.value.length - 1 
    ? currentImageIndex.value + 1 
    : 0
}

// Keyboard navigation handler
const handleKeydown = (e) => {
  if (!lightboxOpen.value) return
  if (e.key === 'Escape') closeLightbox()
  if (e.key === 'ArrowLeft') prevImage()
  if (e.key === 'ArrowRight') nextImage()
}

onMounted(() => {
  window.addEventListener('keydown', handleKeydown)
  if (window.location.hash) {
    setTimeout(() => {
      const element = document.querySelector(window.location.hash)
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' })
      }
    }, 100)
  }
})

onUnmounted(() => {
  window.removeEventListener('keydown', handleKeydown)
})

// Inquiry form
const inquiryForm = ref({
  firstName: '',
  lastName: '',
  email: '',
  phone: '',
  message: '',
  preferredTime: '',
  agreement: false
})

const handleInquirySubmit = () => {
  console.log('Inquiry submitted:', inquiryForm.value)
  alert(`Thank you for your interest in the ${car.value?.name}! We will contact you shortly.`)
  inquiryForm.value = { 
    firstName: '', 
    lastName: '', 
    email: '', 
    phone: '', 
    message: '', 
    preferredTime: '', 
    agreement: false 
  }
}

const handleImageError = (event) => {
  event.target.src = DEFAULT_CAR_IMAGE
}
</script>