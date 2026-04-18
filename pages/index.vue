<template>
  <div>
    <!-- Video Background - Fixed to cover entire viewport -->
    <div class="fixed top-0 left-0 w-full h-screen z-0 pointer-events-none">
      <video 
        autoplay 
        loop 
        muted 
        playsinline
        class="w-full h-full object-cover"
      >
        <source src="/video/heroVideo.mp4" type="video/mp4">
        <!-- Fallback image if video doesn't load -->
        <img 
          src="https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=1920&auto=format&fit=crop"
          alt="Luxury Japanese Car"
          class="w-full h-full object-cover"
        />
      </video>
      <!-- Darker overlay for better text contrast -->
      <div class="absolute inset-0 bg-gradient-to-r from-black/80 via-black/50 to-transparent"></div>
    </div>

    <!-- Hero Section - Content Only -->
    <section class="relative min-h-screen flex items-center z-10 pb-32">
      <!-- Hero Content -->
      <div class="container mx-auto relative py-20">
        <div class="max-w-4xl">
          <!-- Innovation/Trust Badge -->
          <div class="mb-8 flex items-center gap-3">
            <span class="text-white text-sm font-light tracking-[0.3em] uppercase">Since 2020</span>
            <span class="w-12 h-[1px] bg-primary"></span>
            <span class="text-white text-sm font-light tracking-[0.3em] uppercase">Premium Import</span>
          </div>
          
          <!-- Main Headline -->
          <h1 class="text-5xl md:text-7xl lg:text-8xl font-bold text-white mb-6 leading-[1.1]">
            Bangladesh's Premium<br />
            Destination for<br />
            <span class="text-primary">Japanese Cars</span>
          </h1>
          
          <!-- Supporting Text -->
          <p class="text-lg md:text-xl text-white/80 mb-10 max-w-xl leading-relaxed">
            Direct from Japan Auctions. Fully Verified. Delivered with Confidence.
          </p>
          
          <!-- CTA Buttons -->
          <div class="flex flex-wrap gap-4">
            <NuxtLink 
              to="/stock" 
              class="group relative inline-flex items-center gap-3 bg-primary text-white px-8 py-4 font-semibold text-sm uppercase tracking-wider hover:bg-white hover:text-dark transition-all duration-300"
            >
              <span>Browse Available Cars</span>
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 group-hover:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
              </svg>
            </NuxtLink>
            
            <a 
              href="https://wa.me/8809617703704" 
              target="_blank" 
              class="group inline-flex items-center gap-3 border border-white/30 text-white px-8 py-4 font-semibold text-sm uppercase tracking-wider hover:border-primary hover:bg-primary transition-all duration-300"
            >
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
                <path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.582 2.128 2.182-.573c.978.58 1.911.928 3.145.929 3.178 0 5.767-2.587 5.768-5.766.001-3.187-2.575-5.77-5.764-5.771z"/>
              </svg>
              <span>WhatsApp Assistance</span>
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 group-hover:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
              </svg>
            </a>
            
            <NuxtLink 
              to="/prebook" 
              class="group inline-flex items-center gap-3 border border-white/30 text-white px-8 py-4 font-semibold text-sm uppercase tracking-wider hover:border-primary hover:bg-primary transition-all duration-300"
            >
              <span>Prebook Your Car</span>
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

    <!-- Search Bar Section - Overlapping Hero and Trust Strip -->
    <section class="relative z-20 -mt-20 pb-8">
      <div class="container mx-auto">
        <div class="bg-white shadow-2xl max-w-6xl mx-auto">
          <form @submit.prevent="handleSearch" class="p-8">
            <!-- Top Row: Selects -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-6">
              <!-- Make Select -->
              <div>
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">SELECT MAKE</label>
                <select 
                  v-model="searchForm.make"
                  class="w-full px-4 py-4 border-0 border-b-2 border-gray-200 focus:border-primary focus:outline-none bg-transparent text-dark font-medium"
                >
                  <option value="">All Makes</option>
                  <option value="toyota">Toyota</option>
                  <option value="honda">Honda</option>
                  <option value="nissan">Nissan</option>
                  <option value="mitsubishi">Mitsubishi</option>
                  <option value="mazda">Mazda</option>
                  <option value="subaru">Subaru</option>
                  <option value="lexus">Lexus</option>
                </select>
              </div>
              
              <!-- Model Select -->
              <div>
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">SELECT MODEL</label>
                <select 
                  v-model="searchForm.model"
                  class="w-full px-4 py-4 border-0 border-b-2 border-gray-200 focus:border-primary focus:outline-none bg-transparent text-dark font-medium"
                >
                  <option value="">All Models</option>
                  <option value="corolla-cross">Corolla Cross</option>
                  <option value="axio-hybrid">Axio Hybrid</option>
                  <option value="fielder-hybrid">Fielder Hybrid</option>
                  <option value="noah">Noah</option>
                  <option value="voxy">Voxy</option>
                  <option value="harrier">Harrier</option>
                  <option value="land-cruiser">Land Cruiser</option>
                </select>
              </div>
              
              <!-- Body Style -->
              <div>
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">SELECT BODY STYLE</label>
                <select 
                  v-model="searchForm.bodyStyle"
                  class="w-full px-4 py-4 border-0 border-b-2 border-gray-200 focus:border-primary focus:outline-none bg-transparent text-dark font-medium"
                >
                  <option value="">All Body</option>
                  <option value="sedan">Sedan</option>
                  <option value="suv">SUV</option>
                  <option value="hatchback">Hatchback</option>
                  <option value="wagon">Wagon</option>
                  <option value="coupe">Coupe</option>
                  <option value="minivan">Minivan</option>
                </select>
              </div>
            </div>
            
            <!-- Bottom Row: Price Range and Button -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6 items-end">
              <!-- Price Range with Slider -->
              <div>
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">PRICE RANGE</label>
                <div class="flex items-center gap-4">
                  <span class="text-dark font-semibold">{{ formatPrice(minPrice) }}</span>
                  <span class="text-gray-400">-</span>
                  <span class="text-dark font-semibold">{{ formatPrice(maxPrice) }}</span>
                </div>
                <!-- Price Slider -->
                <div class="mt-6 px-2">
                  <div class="relative h-1 bg-gray-200 rounded-full">
                    <!-- Slider Track Fill -->
                    <div 
                      class="absolute h-1 bg-primary rounded-full"
                      :style="{ 
                        left: `${(minPrice / MAX_PRICE) * 100}%`, 
                        width: `${((maxPrice - minPrice) / MAX_PRICE) * 100}%` 
                      }"
                    ></div>
                    
                    <!-- Min Price Slider -->
                    <input 
                      type="range"
                      v-model="minPrice"
                      :min="0" 
                      :max="MAX_PRICE" 
                      step="50000"
                      class="price-slider price-slider-min"
                    />
                    
                    <!-- Max Price Slider -->
                    <input 
                      type="range"
                      v-model="maxPrice"
                      :min="0" 
                      :max="MAX_PRICE" 
                      step="50000"
                      class="price-slider price-slider-max"
                    />
                  </div>
                </div>
              </div>
              
              <!-- View All Listings Button -->
              <div class="flex justify-end">
                <button 
                  type="submit"
                  class="bg-dark text-white px-10 py-4 font-semibold text-sm uppercase tracking-wider hover:bg-primary transition-all duration-300 flex items-center gap-2"
                >
                  VIEW ALL LISTINGS
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
                  </svg>
                </button>
              </div>
            </div>
          </form>
        </div>
      </div>
    </section>

    <!-- Trust Strip -->
    <section class="relative z-10 bg-dark text-white py-8">
      <div class="container mx-auto">
        <div class="grid grid-cols-2 md:grid-cols-5 gap-6 text-center">
          <div class="flex flex-col items-center gap-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z" />
            </svg>
            <span class="text-sm font-medium">Auction Grade Verified</span>
          </div>
          <div class="flex flex-col items-center gap-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
            <span class="text-sm font-medium">Japan Direct Sourcing</span>
          </div>
          <div class="flex flex-col items-center gap-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" />
            </svg>
            <span class="text-sm font-medium">Full Inspection Transparency</span>
          </div>
          <div class="flex flex-col items-center gap-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4" />
            </svg>
            <span class="text-sm font-medium">BRTA Support</span>
          </div>
          <div class="flex flex-col items-center gap-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
            <span class="text-sm font-medium">3-Year Care Plan Available</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Our Models Section -->
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
          <!-- Navigation Arrows -->
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

          <!-- Car Images Carousel - No Cards, Just Images -->
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
                <!-- No Card - Just Image and Text -->
                <div class="relative group text-center">
                  <!-- Car Image - No Background -->
                  <div class="relative overflow-hidden mb-4">
                    <img 
                      :src="car.image" 
                      :alt="car.name"
                      class="w-full h-auto object-contain group-hover:scale-105 transition-transform duration-500"
                    />
                    
                    <!-- Book a Test Drive - Appears on Hover -->
                    <div class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300">
                      <NuxtLink 
                        :to="`/book-test-drive?car=${car.id}`" 
                        class="bg-primary text-white px-6 py-3 rounded-full font-semibold text-sm uppercase tracking-wider hover:bg-dark transition-all duration-300"
                      >
                        Book a Test Drive
                      </NuxtLink>
                    </div>
                  </div>
                  
                  <!-- Car Name -->
                  <h3 class="text-xl font-bold mb-3 text-dark">
                    {{ car.name }}
                  </h3>
                  
                  <!-- Learn More - Always Visible -->
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
          
          <!-- Pagination Dots -->
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
        
        <!-- View All Link -->
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

    <!-- About Section -->
    <section class="relative z-10 py-20 bg-gray-50">
      <div class="container mx-auto">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
          <!-- Left Content -->
          <div>
            <p class="section-subtitle">Making Car Import Safe & Transparent</p>
            <h2 class="section-title">About CarBDShop</h2>
            <p class="text-gray-600 mb-6 leading-relaxed">
              We source vehicles directly from Japanese auctions, focusing exclusively on high-quality vehicles with verified auction grades (Grade 4 / 4.5 / 5). Every vehicle comes with complete transparency in pricing, inspection reports, and the entire import process.
            </p>
            <p class="text-gray-600 mb-8 leading-relaxed">
              Our mission is simple: <span class="font-semibold text-dark">Making car import safe, transparent, and premium.</span>
            </p>
            
            <!-- Key Points -->
            <div class="grid grid-cols-2 gap-4">
              <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
                <span class="text-dark font-medium">Grade 4/4.5/5 Only</span>
              </div>
              <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
                <span class="text-dark font-medium">Full Transparency</span>
              </div>
              <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
                <span class="text-dark font-medium">Auction Verified</span>
              </div>
              <div class="flex items-center gap-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
                <span class="text-dark font-medium">Premium Service</span>
              </div>
            </div>
          </div>
          
          <!-- Right Image -->
          <div class="relative">
            <img 
              src="https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=800&auto=format&fit=crop" 
              alt="About CarBDShop" 
              class="w-full h-auto shadow-2xl"
            />
            <div class="absolute -bottom-6 -right-6 bg-primary text-white p-6 hidden lg:block">
              <p class="text-3xl font-bold">500+</p>
              <p class="text-sm uppercase tracking-wider">Cars Imported</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- How It Works Section -->
    <section class="relative z-10 py-20 bg-white">
      <div class="container mx-auto">
        <div class="text-center mb-12">
          <p class="section-subtitle">Simple & Transparent Process</p>
          <h2 class="section-title">How It Works</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            From selection to delivery, we handle everything with complete transparency.
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <!-- Step 1 -->
          <div class="text-center group">
            <div class="w-20 h-20 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4 group-hover:bg-primary transition-all duration-300">
              <span class="text-primary text-2xl font-bold group-hover:text-white">1</span>
            </div>
            <h3 class="text-xl font-bold mb-3">Choose / Prebook</h3>
            <p class="text-gray-600">
              Select from upcoming inventory or request a custom car tailored to your needs.
            </p>
          </div>
          
          <!-- Step 2 -->
          <div class="text-center group">
            <div class="w-20 h-20 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4 group-hover:bg-primary transition-all duration-300">
              <span class="text-primary text-2xl font-bold group-hover:text-white">2</span>
            </div>
            <h3 class="text-xl font-bold mb-3">Auction Verification</h3>
            <p class="text-gray-600">
              We provide auction sheet, grade, and complete inspection details for transparency.
            </p>
          </div>
          
          <!-- Step 3 -->
          <div class="text-center group">
            <div class="w-20 h-20 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4 group-hover:bg-primary transition-all duration-300">
              <span class="text-primary text-2xl font-bold group-hover:text-white">3</span>
            </div>
            <h3 class="text-xl font-bold mb-3">Secure & Ship</h3>
            <p class="text-gray-600">
              We handle the purchase, shipping, and complete import process for you.
            </p>
          </div>
          
          <!-- Step 4 -->
          <div class="text-center group">
            <div class="w-20 h-20 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4 group-hover:bg-primary transition-all duration-300">
              <span class="text-primary text-2xl font-bold group-hover:text-white">4</span>
            </div>
            <h3 class="text-xl font-bold mb-3">Delivery & Support</h3>
            <p class="text-gray-600">
              Receive your vehicle with complete documentation and ongoing support.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Why Choose Us Section -->
    <section class="relative z-10 py-20 bg-dark">
      <div class="container mx-auto">
        <div class="text-center mb-12">
          <p class="section-subtitle text-primary">Why CarBDShop</p>
          <h2 class="section-title text-white">Why Choose Us</h2>
          <p class="text-white/60 max-w-2xl mx-auto">
            We're committed to providing the best Japanese car import experience in Bangladesh.
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-5 gap-6">
          <div class="text-center p-6 border border-white/10 hover:border-primary transition-all duration-300">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-primary mx-auto mb-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
            <h3 class="text-white font-bold mb-2">Japan Direct Access</h3>
            <p class="text-white/60 text-sm">No middlemen, ensuring better quality and pricing.</p>
          </div>
          
          <div class="text-center p-6 border border-white/10 hover:border-primary transition-all duration-300">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-primary mx-auto mb-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z" />
            </svg>
            <h3 class="text-white font-bold mb-2">Grade Transparency</h3>
            <p class="text-white/60 text-sm">Verified auction grading for every vehicle.</p>
          </div>
          
          <div class="text-center p-6 border border-white/10 hover:border-primary transition-all duration-300">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-primary mx-auto mb-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
            <h3 class="text-white font-bold mb-2">Market-Driven Pricing</h3>
            <p class="text-white/60 text-sm">Competitive pricing tailored to Bangladesh market.</p>
          </div>
          
          <div class="text-center p-6 border border-white/10 hover:border-primary transition-all duration-300">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-primary mx-auto mb-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M18.364 5.636l-3.536 3.536m0 5.656l3.536 3.536M9.172 9.172L5.636 5.636m3.536 9.9l-3.536 3.535M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 16v-4l-2-2" />
            </svg>
            <h3 class="text-white font-bold mb-2">After-Sales Support</h3>
            <p class="text-white/60 text-sm">Care plans and inspection services available.</p>
          </div>
          
          <div class="text-center p-6 border border-white/10 hover:border-primary transition-all duration-300">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-primary mx-auto mb-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
            </svg>
            <h3 class="text-white font-bold mb-2">Fast Prebooking</h3>
            <p class="text-white/60 text-sm">Secure your desired car before it arrives.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Pre-Booking & Trade-In Forms Section -->
    <section class="relative z-10 py-20 bg-white">
      <div class="container mx-auto">
        <div class="text-center mb-12">
          <p class="section-subtitle">Get Started Today</p>
          <h2 class="section-title">Pre-Book or Trade-In</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Secure your dream car before it arrives or trade in your current vehicle for a great deal.
          </p>
        </div>

        <!-- Tabbed Forms - Similar to REQUEST A QUOTE / TRACK & TRACE -->
        <div class="max-w-5xl mx-auto">
          <!-- Form Tabs -->
          <div class="flex justify-center gap-4 mb-8">
            <button 
              @click="activeForm = 'prebook'"
              class="px-8 py-4 font-semibold text-sm uppercase tracking-wider transition-all duration-300 flex items-center gap-2"
              :class="activeForm === 'prebook' 
                ? 'bg-primary text-white' 
                : 'bg-gray-100 text-dark hover:bg-gray-200'"
            >
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
              </svg>
              PRE-BOOK A CAR
            </button>
            <button 
              @click="activeForm = 'tradein'"
              class="px-8 py-4 font-semibold text-sm uppercase tracking-wider transition-all duration-300 flex items-center gap-2"
              :class="activeForm === 'tradein' 
                ? 'bg-primary text-white' 
                : 'bg-gray-100 text-dark hover:bg-gray-200'"
            >
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7h12m0 0l-4-4m4 4l-4 4m0 6H4m0 0l4 4m-4-4l4-4" />
              </svg>
              TRADE-IN YOUR CAR
            </button>
          </div>

          <!-- Pre-Booking Form -->
          <div v-show="activeForm === 'prebook'" class="bg-white shadow-xl p-8">
            <form @submit.prevent="handlePrebookSubmit" class="space-y-6">
              <h3 class="text-xl font-bold text-dark mb-6 flex items-center gap-3">
                <span class="w-8 h-[2px] bg-primary"></span>
                Pre-Booking Information
              </h3>
              
              <!-- Personal Information -->
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Full Name *</label>
                  <input 
                    type="text" 
                    v-model="prebookForm.fullName"
                    required
                    placeholder="Enter your full name"
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  />
                </div>
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Phone Number *</label>
                  <input 
                    type="tel" 
                    v-model="prebookForm.phone"
                    required
                    placeholder="Enter your phone number"
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  />
                </div>
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Email Address *</label>
                  <input 
                    type="email" 
                    v-model="prebookForm.email"
                    required
                    placeholder="Enter your email"
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  />
                </div>
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Preferred Car Model *</label>
                  <select 
                    v-model="prebookForm.carModel"
                    required
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  >
                    <option value="">Select Model</option>
                    <option value="corolla-cross">Toyota Corolla Cross</option>
                    <option value="axio-hybrid">Toyota Axio Hybrid</option>
                    <option value="fielder-hybrid">Toyota Fielder Hybrid</option>
                    <option value="noah">Toyota Noah</option>
                    <option value="voxy">Toyota Voxy</option>
                    <option value="harrier">Toyota Harrier</option>
                    <option value="premium-suv">Premium SUV</option>
                    <option value="other">Other (Specify in message)</option>
                  </select>
                </div>
              </div>

              <!-- Additional Details -->
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Preferred Budget Range</label>
                  <select 
                    v-model="prebookForm.budget"
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  >
                    <option value="">Select Budget Range</option>
                    <option value="20-30">20-30 Lakh</option>
                    <option value="30-40">30-40 Lakh</option>
                    <option value="40-50">40-50 Lakh</option>
                    <option value="50-70">50-70 Lakh</option>
                    <option value="70+">70 Lakh+</option>
                  </select>
                </div>
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Expected Purchase Timeline</label>
                  <select 
                    v-model="prebookForm.timeline"
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  >
                    <option value="">Select Timeline</option>
                    <option value="1-month">Within 1 Month</option>
                    <option value="3-months">1-3 Months</option>
                    <option value="6-months">3-6 Months</option>
                    <option value="exploring">Just Exploring</option>
                  </select>
                </div>
              </div>

              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Additional Message (Optional)</label>
                <textarea 
                  v-model="prebookForm.message"
                  rows="4"
                  placeholder="Any specific requirements or questions..."
                  class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark resize-none"
                ></textarea>
              </div>

              <!-- Agreement -->
              <div class="flex items-center gap-3">
                <input 
                  type="checkbox" 
                  v-model="prebookForm.agreement"
                  required
                  class="w-4 h-4 text-primary border-gray-300 focus:ring-primary"
                />
                <label class="text-sm text-gray-600">
                  I agree to be contacted by CarBDShop regarding my pre-booking inquiry.
                </label>
              </div>

              <div class="flex justify-end pt-4">
                <button 
                  type="submit"
                  class="bg-dark text-white px-10 py-4 font-semibold text-sm uppercase tracking-wider hover:bg-primary transition-all duration-300 flex items-center gap-2"
                >
                  SUBMIT PRE-BOOKING
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
                  </svg>
                </button>
              </div>
            </form>
          </div>

          <!-- Trade-In Form -->
          <div v-show="activeForm === 'tradein'" class="bg-white shadow-xl p-8">
            <form @submit.prevent="handleTradeinSubmit" class="space-y-6">
              <h3 class="text-xl font-bold text-dark mb-6 flex items-center gap-3">
                <span class="w-8 h-[2px] bg-primary"></span>
                Trade-In Information
              </h3>
              
              <!-- Personal Information -->
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Full Name *</label>
                  <input 
                    type="text" 
                    v-model="tradeinForm.fullName"
                    required
                    placeholder="Enter your full name"
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  />
                </div>
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Phone Number *</label>
                  <input 
                    type="tel" 
                    v-model="tradeinForm.phone"
                    required
                    placeholder="Enter your phone number"
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  />
                </div>
              </div>

              <!-- Vehicle Information -->
              <h4 class="text-lg font-bold text-dark pt-4">Vehicle Details</h4>
              <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Car Model *</label>
                  <input 
                    type="text" 
                    v-model="tradeinForm.carModel"
                    required
                    placeholder="e.g., Toyota Axio"
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  />
                </div>
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Registration Year *</label>
                  <select 
                    v-model="tradeinForm.year"
                    required
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  >
                    <option value="">Select Year</option>
                    <option value="2024">2024</option>
                    <option value="2023">2023</option>
                    <option value="2022">2022</option>
                    <option value="2021">2021</option>
                    <option value="2020">2020</option>
                    <option value="2019">2019</option>
                    <option value="2018">2018</option>
                    <option value="older">Older</option>
                  </select>
                </div>
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Mileage (km) *</label>
                  <input 
                    type="number" 
                    v-model="tradeinForm.mileage"
                    required
                    placeholder="Enter mileage"
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  />
                </div>
              </div>

              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Asking Price (BDT) *</label>
                  <input 
                    type="number" 
                    v-model="tradeinForm.askingPrice"
                    required
                    placeholder="Enter your asking price"
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  />
                </div>
                <div class="form-group">
                  <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Condition</label>
                  <select 
                    v-model="tradeinForm.condition"
                    class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark"
                  >
                    <option value="">Select Condition</option>
                    <option value="excellent">Excellent</option>
                    <option value="good">Good</option>
                    <option value="fair">Fair</option>
                    <option value="needs-work">Needs Work</option>
                  </select>
                </div>
              </div>

              <!-- Image Upload Info -->
              <div class="bg-gray-50 p-4 border border-gray-200">
                <p class="text-sm text-gray-600 mb-2">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 inline mr-1 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" />
                  </svg>
                  <strong>Image Upload:</strong> After submission, we'll contact you to request up to 5 images (max 2MB each, JPG/PNG format).
                </p>
              </div>

              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Additional Notes (Optional)</label>
                <textarea 
                  v-model="tradeinForm.notes"
                  rows="3"
                  placeholder="Any additional information about your vehicle..."
                  class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark resize-none"
                ></textarea>
              </div>

              <!-- CAPTCHA Placeholder -->
              <div class="bg-gray-50 p-4 border border-gray-200 flex items-center gap-4">
                <div class="flex items-center gap-2">
                  <input type="checkbox" required class="w-4 h-4 text-primary" />
                  <span class="text-sm text-gray-600">I'm not a robot</span>
                </div>
                <div class="text-xs text-gray-400">reCAPTCHA</div>
              </div>

              <div class="flex justify-end pt-4">
                <button 
                  type="submit"
                  class="bg-dark text-white px-10 py-4 font-semibold text-sm uppercase tracking-wider hover:bg-primary transition-all duration-300 flex items-center gap-2"
                >
                  SUBMIT TRADE-IN REQUEST
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
                  </svg>
                </button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </section>

    <!-- Auto Loan Calculator Section -->
    <section class="relative z-10 py-20 bg-gray-50">
      <div class="container mx-auto">
        <div class="text-center mb-12">
          <p class="section-subtitle">Plan Your Purchase</p>
          <h2 class="section-title">Auto Loan Calculator</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Use our calculator to estimate your monthly car payments.
          </p>
        </div>

        <div class="max-w-4xl mx-auto">
          <div class="bg-white shadow-xl p-8 md:p-10">
            <!-- Total Price -->
            <div class="mb-8">
              <label class="block text-sm font-semibold text-dark mb-2">Total Price</label>
              <div class="flex items-center gap-4">
                <span class="text-2xl font-bold text-dark">৳</span>
                <input 
                  type="number" 
                  v-model="calculatorForm.carPrice"
                  min="0"
                  step="50000"
                  class="w-full px-4 py-3 text-2xl font-bold border-0 border-b-2 border-gray-200 focus:border-primary focus:outline-none bg-transparent text-dark"
                  placeholder="Enter car price"
                />
              </div>
            </div>

            <!-- Down Payment & Interest Rate Row -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-8">
              <!-- Down Payment -->
              <div>
                <div class="flex justify-between items-center mb-2">
                  <label class="block text-sm font-semibold text-dark">Down Payment</label>
                  <span class="text-primary font-bold">{{ downPaymentPercentage }}%</span>
                </div>
                <input 
                  type="range" 
                  v-model="downPaymentPercentage"
                  min="0"
                  max="50"
                  step="1"
                  class="w-full h-1 bg-gray-200 rounded-full appearance-none cursor-pointer [&::-webkit-slider-thumb]:appearance-none [&::-webkit-slider-thumb]:w-5 [&::-webkit-slider-thumb]:h-5 [&::-webkit-slider-thumb]:bg-primary [&::-webkit-slider-thumb]:rounded-full [&::-webkit-slider-thumb]:cursor-pointer [&::-webkit-slider-thumb]:border-2 [&::-webkit-slider-thumb]:border-white [&::-webkit-slider-thumb]:shadow-md"
                />
                <div class="flex justify-between text-xs text-gray-500 mt-1">
                  <span>0%</span>
                  <span>25%</span>
                  <span>50%</span>
                </div>
              </div>

              <!-- Loan Term (Months) -->
              <div>
                <div class="flex justify-between items-center mb-2">
                  <label class="block text-sm font-semibold text-dark">Loan Term</label>
                  <span class="text-primary font-bold">{{ calculatorForm.loanTerm }} months</span>
                </div>
                <input 
                  type="range" 
                  v-model="calculatorForm.loanTerm"
                  min="12"
                  max="60"
                  step="12"
                  class="w-full h-1 bg-gray-200 rounded-full appearance-none cursor-pointer [&::-webkit-slider-thumb]:appearance-none [&::-webkit-slider-thumb]:w-5 [&::-webkit-slider-thumb]:h-5 [&::-webkit-slider-thumb]:bg-primary [&::-webkit-slider-thumb]:rounded-full [&::-webkit-slider-thumb]:cursor-pointer [&::-webkit-slider-thumb]:border-2 [&::-webkit-slider-thumb]:border-white [&::-webkit-slider-thumb]:shadow-md"
                />
                <div class="flex justify-between text-xs text-gray-500 mt-1">
                  <span>12 mo</span>
                  <span>24 mo</span>
                  <span>36 mo</span>
                  <span>48 mo</span>
                  <span>60 mo</span>
                </div>
              </div>
            </div>

            <!-- Interest Rate & Monthly Payment Row -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-8">
              <!-- Interest Rate -->
              <div>
                <div class="flex justify-between items-center mb-2">
                  <label class="block text-sm font-semibold text-dark">Interest Rate</label>
                  <span class="text-primary font-bold">{{ calculatorForm.interestRate }}%</span>
                </div>
                <input 
                  type="range" 
                  v-model="calculatorForm.interestRate"
                  min="0"
                  max="15"
                  step="0.5"
                  class="w-full h-1 bg-gray-200 rounded-full appearance-none cursor-pointer [&::-webkit-slider-thumb]:appearance-none [&::-webkit-slider-thumb]:w-5 [&::-webkit-slider-thumb]:h-5 [&::-webkit-slider-thumb]:bg-primary [&::-webkit-slider-thumb]:rounded-full [&::-webkit-slider-thumb]:cursor-pointer [&::-webkit-slider-thumb]:border-2 [&::-webkit-slider-thumb]:border-white [&::-webkit-slider-thumb]:shadow-md"
                />
                <div class="flex justify-between text-xs text-gray-500 mt-1">
                  <span>0%</span>
                  <span>5%</span>
                  <span>10%</span>
                  <span>15%</span>
                </div>
              </div>

              <!-- Monthly Payment Display -->
              <div class="bg-gray-50 p-6 border border-gray-200">
                <p class="text-sm text-gray-500 mb-2">Monthly Payment</p>
                <p class="text-4xl font-bold text-primary">{{ formatPrice(monthlyPayment) }}</p>
                <p class="text-xs text-gray-400 mt-2">per month</p>
              </div>
            </div>

            <!-- Calculation Details -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 pt-6 border-t border-gray-200">
              <div>
                <p class="text-xs text-gray-500 uppercase tracking-wider mb-1">Down Payment Amount</p>
                <p class="text-xl font-bold text-dark">{{ formatPrice(downPaymentAmount) }}</p>
              </div>
              <div>
                <p class="text-xs text-gray-500 uppercase tracking-wider mb-1">Amount Financed</p>
                <p class="text-xl font-bold text-dark">{{ formatPrice(amountFinanced) }}</p>
              </div>
              <div>
                <p class="text-xs text-gray-500 uppercase tracking-wider mb-1">Total Interest</p>
                <p class="text-xl font-bold text-dark">{{ formatPrice(totalInterest) }}</p>
              </div>
            </div>

            <!-- Apply for Loan Button -->
            <div class="flex justify-center mt-10">
              <button 
                @click="handleLoanApplication"
                class="bg-primary text-white px-10 py-4 font-semibold text-sm uppercase tracking-wider hover:bg-dark transition-all duration-300 flex items-center gap-2"
              >
                Apply for a Loan
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
                </svg>
              </button>
            </div>

            <!-- Bank Comparison Note -->
            <p class="text-center text-xs text-gray-400 mt-6">
              * Multiple banks available for comparison. Contact us for personalized loan options.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Featured Categories / Prebooking Section -->
    <section class="relative z-10 py-20 bg-white">
      <div class="container mx-auto">
        <div class="text-center mb-12">
          <p class="section-subtitle">Secure Your Car Before Arrival</p>
          <h2 class="section-title">Featured Categories</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Stock arriving soon - Prebook now to secure your vehicle.
          </p>
        </div>
        
        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-4">
          <div class="text-center p-6 border border-gray-200 hover:border-primary hover:shadow-lg transition-all duration-300 bg-white">
            <h3 class="text-lg font-bold mb-2">Corolla Cross</h3>
            <p class="text-primary text-sm font-medium mb-3">Stock arriving soon</p>
            <NuxtLink to="/prebook" class="text-dark text-sm font-medium hover:text-primary transition-colors inline-flex items-center gap-1">
              Prebook now →
            </NuxtLink>
          </div>
          
          <div class="text-center p-6 border border-gray-200 hover:border-primary hover:shadow-lg transition-all duration-300 bg-white">
            <h3 class="text-lg font-bold mb-2">Axio Hybrid</h3>
            <p class="text-primary text-sm font-medium mb-3">Stock arriving soon</p>
            <NuxtLink to="/prebook" class="text-dark text-sm font-medium hover:text-primary transition-colors inline-flex items-center gap-1">
              Prebook now →
            </NuxtLink>
          </div>
          
          <div class="text-center p-6 border border-gray-200 hover:border-primary hover:shadow-lg transition-all duration-300 bg-white">
            <h3 class="text-lg font-bold mb-2">Fielder Hybrid</h3>
            <p class="text-primary text-sm font-medium mb-3">Stock arriving soon</p>
            <NuxtLink to="/prebook" class="text-dark text-sm font-medium hover:text-primary transition-colors inline-flex items-center gap-1">
              Prebook now →
            </NuxtLink>
          </div>
          
          <div class="text-center p-6 border border-gray-200 hover:border-primary hover:shadow-lg transition-all duration-300 bg-white">
            <h3 class="text-lg font-bold mb-2">Noah / Voxy</h3>
            <p class="text-primary text-sm font-medium mb-3">Stock arriving soon</p>
            <NuxtLink to="/prebook" class="text-dark text-sm font-medium hover:text-primary transition-colors inline-flex items-center gap-1">
              Prebook now →
            </NuxtLink>
          </div>
          
          <div class="text-center p-6 border border-gray-200 hover:border-primary hover:shadow-lg transition-all duration-300 bg-white">
            <h3 class="text-lg font-bold mb-2">Premium SUVs</h3>
            <p class="text-primary text-sm font-medium mb-3">Stock arriving soon</p>
            <NuxtLink to="/prebook" class="text-dark text-sm font-medium hover:text-primary transition-colors inline-flex items-center gap-1">
              Prebook now →
            </NuxtLink>
          </div>
        </div>
        
        <!-- Urgency CTA -->
        <div class="text-center mt-10">
          <a 
            href="https://wa.me/8809617703704" 
            target="_blank"
            class="inline-flex items-center gap-2 bg-primary text-white px-8 py-4 font-semibold text-sm uppercase tracking-wider hover:bg-dark transition-all duration-300"
          >
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
              <path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.582 2.128 2.182-.573c.978.58 1.911.928 3.145.929 3.178 0 5.767-2.587 5.768-5.766.001-3.187-2.575-5.77-5.764-5.771z"/>
            </svg>
            Prebook via WhatsApp
          </a>
        </div>
      </div>
    </section>

    <!-- Blog Section Preview -->
    <section class="relative z-10 py-20 bg-gray-50">
      <div class="container mx-auto">
        <div class="flex justify-between items-center mb-12">
          <div>
            <p class="section-subtitle">Stay Informed</p>
            <h2 class="section-title">Latest from Our Blog</h2>
          </div>
          <NuxtLink to="/blog" class="text-primary font-semibold hover:text-dark transition-colors inline-flex items-center gap-2">
            View All Articles
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
            </svg>
          </NuxtLink>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <!-- Blog Card 1 -->
          <div class="bg-white shadow-sm hover:shadow-lg transition-all duration-300 border border-gray-100">
            <div class="overflow-hidden">
              <img 
                src="https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=600&auto=format&fit=crop" 
                alt="Blog post" 
                class="w-full h-48 object-cover hover:scale-105 transition-transform duration-500"
              />
            </div>
            <div class="p-6">
              <div class="flex items-center gap-4 text-sm text-gray-500 mb-3">
                <span class="bg-primary/10 text-primary px-2 py-1 text-xs font-semibold uppercase">Guides</span>
                <span>Oct 16, 2024</span>
              </div>
              <h3 class="text-lg font-bold mb-3 hover:text-primary transition-colors">
                <NuxtLink to="/blog/1">Complete Guide to Japanese Car Auctions</NuxtLink>
              </h3>
              <p class="text-gray-600 text-sm mb-4">
                Learn how Japanese car auctions work and how to get the best deals on quality vehicles.
              </p>
              <NuxtLink to="/blog/1" class="text-primary font-medium hover:text-dark transition-colors inline-flex items-center gap-1">
                Read More →
              </NuxtLink>
            </div>
          </div>
          
          <!-- Blog Card 2 -->
          <div class="bg-white shadow-sm hover:shadow-lg transition-all duration-300 border border-gray-100">
            <div class="overflow-hidden">
              <img 
                src="https://images.unsplash.com/photo-1581540222194-0d38b4d8a7d0?q=80&w=600&auto=format&fit=crop" 
                alt="Blog post" 
                class="w-full h-48 object-cover hover:scale-105 transition-transform duration-500"
              />
            </div>
            <div class="p-6">
              <div class="flex items-center gap-4 text-sm text-gray-500 mb-3">
                <span class="bg-primary/10 text-primary px-2 py-1 text-xs font-semibold uppercase">Import</span>
                <span>Oct 14, 2024</span>
              </div>
              <h3 class="text-lg font-bold mb-3 hover:text-primary transition-colors">
                <NuxtLink to="/blog/2">Bangladesh Car Import Process Explained</NuxtLink>
              </h3>
              <p class="text-gray-600 text-sm mb-4">
                Step-by-step breakdown of importing a car from Japan to Bangladesh.
              </p>
              <NuxtLink to="/blog/2" class="text-primary font-medium hover:text-dark transition-colors inline-flex items-center gap-1">
                Read More →
              </NuxtLink>
            </div>
          </div>
          
          <!-- Blog Card 3 -->
          <div class="bg-white shadow-sm hover:shadow-lg transition-all duration-300 border border-gray-100">
            <div class="overflow-hidden">
              <img 
                src="https://images.unsplash.com/photo-1568605117036-5fe5e4ba0f5a?q=80&w=600&auto=format&fit=crop" 
                alt="Blog post" 
                class="w-full h-48 object-cover hover:scale-105 transition-transform duration-500"
              />
            </div>
            <div class="p-6">
              <div class="flex items-center gap-4 text-sm text-gray-500 mb-3">
                <span class="bg-primary/10 text-primary px-2 py-1 text-xs font-semibold uppercase">Finance</span>
                <span>Oct 10, 2024</span>
              </div>
              <h3 class="text-lg font-bold mb-3 hover:text-primary transition-colors">
                <NuxtLink to="/blog/3">EMI Calculator: Plan Your Car Purchase</NuxtLink>
              </h3>
              <p class="text-gray-600 text-sm mb-4">
                Use our EMI calculator to plan your finances and find the best loan options.
              </p>
              <NuxtLink to="/blog/3" class="text-primary font-medium hover:text-dark transition-colors inline-flex items-center gap-1">
                Read More →
              </NuxtLink>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact & Showroom Section -->
    <section class="relative z-10 py-20 bg-white">
      <div class="container mx-auto">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
          <!-- Contact Info -->
          <div>
            <p class="section-subtitle">Visit Us</p>
            <h2 class="section-title">Contact & Showroom</h2>
            <p class="text-gray-600 mb-8 leading-relaxed">
              Visit our showroom in Sylhet to see our available vehicles or discuss your import requirements with our experts.
            </p>
            
            <div class="space-y-6">
              <div class="flex items-start gap-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-primary mt-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                </svg>
                <div>
                  <h4 class="font-bold text-dark mb-1">Location</h4>
                  <p class="text-gray-600">Sylhet, Bangladesh</p>
                </div>
              </div>
              
              <div class="flex items-start gap-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-primary mt-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                </svg>
                <div>
                  <h4 class="font-bold text-dark mb-1">Business Hours</h4>
                  <p class="text-gray-600">Sunday - Thursday: 9:00 AM - 8:00 PM</p>
                  <p class="text-gray-600">Friday - Saturday: 10:00 AM - 8:00 PM</p>
                </div>
              </div>
              
              <div class="flex items-start gap-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-primary mt-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                </svg>
                <div>
                  <h4 class="font-bold text-dark mb-1">Phone</h4>
                  <a href="tel:+8809617703704" class="text-primary hover:text-dark transition-colors">09617703704</a>
                </div>
              </div>
            </div>
            
            <div class="mt-8 flex gap-4">
              <a 
                href="https://wa.me/8809617703704" 
                target="_blank"
                class="bg-green-500 text-white px-6 py-3 font-semibold text-sm uppercase tracking-wider hover:bg-green-600 transition-all duration-300 inline-flex items-center gap-2"
              >
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.582 2.128 2.182-.573c.978.58 1.911.928 3.145.929 3.178 0 5.767-2.587 5.768-5.766.001-3.187-2.575-5.77-5.764-5.771z"/>
                </svg>
                WhatsApp
              </a>
              <a 
                href="https://maps.google.com" 
                target="_blank"
                class="border border-dark text-dark px-6 py-3 font-semibold text-sm uppercase tracking-wider hover:bg-dark hover:text-white transition-all duration-300 inline-flex items-center gap-2"
              >
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 20l-5.447-2.724A1 1 0 013 16.382V5.618a1 1 0 011.447-.894L9 7m0 13l6-3m-6 3V7m6 10l4.553 2.276A1 1 0 0021 18.382V7.618a1 1 0 00-.553-.894L15 4m0 13V4m0 0L9 7" />
                </svg>
                Google Map
              </a>
            </div>
          </div>
          
          <!-- Map Placeholder -->
          <div class="bg-gray-200 h-full min-h-[400px] flex items-center justify-center">
            <div class="text-center">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-16 w-16 text-gray-400 mx-auto mb-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 20l-5.447-2.724A1 1 0 013 16.382V5.618a1 1 0 011.447-.894L9 7m0 13l6-3m-6 3V7m6 10l4.553 2.276A1 1 0 0021 18.382V7.618a1 1 0 00-.553-.894L15 4m0 13V4m0 0L9 7" />
              </svg>
              <p class="text-gray-500">Google Map Integration</p>
              <p class="text-gray-400 text-sm mt-2">Sylhet, Bangladesh</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Social Proof / Gallery Section -->
    <section class="relative z-10 py-20 bg-gray-50">
      <div class="container mx-auto">
        <div class="text-center mb-12">
          <p class="section-subtitle">Real Deliveries, Real Customers</p>
          <h2 class="section-title">Social Proof</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            See what our customers say about their CarBDShop experience.
          </p>
        </div>
        
        <!-- Gallery Grid -->
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
          <div class="relative group overflow-hidden">
            <img 
              src="https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=400&auto=format&fit=crop" 
              alt="Delivery" 
              class="w-full h-48 object-cover group-hover:scale-105 transition-transform duration-500"
            />
            <div class="absolute inset-0 bg-dark/50 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
              <span class="text-white font-medium">Delivery Photo</span>
            </div>
          </div>
          <div class="relative group overflow-hidden">
            <img 
              src="https://images.unsplash.com/photo-1581540222194-0d38b4d8a7d0?q=80&w=400&auto=format&fit=crop" 
              alt="Inspection" 
              class="w-full h-48 object-cover group-hover:scale-105 transition-transform duration-500"
            />
            <div class="absolute inset-0 bg-dark/50 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
              <span class="text-white font-medium">Inspection Video</span>
            </div>
          </div>
          <div class="relative group overflow-hidden">
            <img 
              src="https://images.unsplash.com/photo-1568605117036-5fe5e4ba0f5a?q=80&w=400&auto=format&fit=crop" 
              alt="Showroom" 
              class="w-full h-48 object-cover group-hover:scale-105 transition-transform duration-500"
            />
            <div class="absolute inset-0 bg-dark/50 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
              <span class="text-white font-medium">Showroom</span>
            </div>
          </div>
          <div class="relative group overflow-hidden">
            <img 
              src="https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?q=80&w=400&auto=format&fit=crop" 
              alt="Happy Customer" 
              class="w-full h-48 object-cover group-hover:scale-105 transition-transform duration-500"
            />
            <div class="absolute inset-0 bg-dark/50 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
              <span class="text-white font-medium">Happy Customer</span>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted, watch } from 'vue'

// Search form
const searchForm = ref({
  make: '',
  model: '',
  bodyStyle: ''
})

// Price range state
const MAX_PRICE = 10000000 // 1 Crore
const minPrice = ref(0)
const maxPrice = ref(MAX_PRICE)

// Ensure min doesn't exceed max
watch(minPrice, (newVal) => {
  if (newVal > maxPrice.value) {
    minPrice.value = maxPrice.value
  }
})

// Ensure max doesn't go below min
watch(maxPrice, (newVal) => {
  if (newVal < minPrice.value) {
    maxPrice.value = minPrice.value
  }
})

const formatPrice = (value) => {
  if (value >= 10000000) {
    return `৳${(value / 10000000).toFixed(2)} Cr`
  } else if (value >= 100000) {
    return `৳${(value / 100000).toFixed(2)} L`
  }
  return `৳${Math.round(value).toLocaleString()}`
}

const handleSearch = () => {
  console.log('Search:', searchForm.value)
  console.log('Price Range:', minPrice.value, '-', maxPrice.value)
  navigateTo({
    path: '/stock',
    query: {
      ...searchForm.value,
      minPrice: minPrice.value,
      maxPrice: maxPrice.value
    }
  })
}

// Form state for Pre-Booking & Trade-In
const activeForm = ref('prebook')

// Pre-Booking Form
const prebookForm = ref({
  fullName: '',
  phone: '',
  email: '',
  carModel: '',
  budget: '',
  timeline: '',
  message: '',
  agreement: false
})

const handlePrebookSubmit = () => {
  console.log('Pre-booking form submitted:', prebookForm.value)
  // Reset form
  prebookForm.value = {
    fullName: '',
    phone: '',
    email: '',
    carModel: '',
    budget: '',
    timeline: '',
    message: '',
    agreement: false
  }
  alert('Thank you for your pre-booking request! We will contact you shortly.')
}

// Trade-In Form
const tradeinForm = ref({
  fullName: '',
  phone: '',
  carModel: '',
  year: '',
  mileage: '',
  askingPrice: '',
  condition: '',
  notes: ''
})

const handleTradeinSubmit = () => {
  console.log('Trade-in form submitted:', tradeinForm.value)
  // Reset form
  tradeinForm.value = {
    fullName: '',
    phone: '',
    carModel: '',
    year: '',
    mileage: '',
    askingPrice: '',
    condition: '',
    notes: ''
  }
  alert('Thank you for your trade-in request! We will contact you shortly to request vehicle images.')
}

// Auto Loan Calculator
const calculatorForm = ref({
  carPrice: 2500000, // Default: 25 Lakh
  loanTerm: 48, // Default: 48 months
  interestRate: 9 // Default: 9%
})

const downPaymentPercentage = ref(20) // Default: 20%

// Computed values for calculator
const downPaymentAmount = computed(() => {
  return (calculatorForm.value.carPrice * downPaymentPercentage.value) / 100
})

const amountFinanced = computed(() => {
  return calculatorForm.value.carPrice - downPaymentAmount.value
})

const monthlyInterestRate = computed(() => {
  return calculatorForm.value.interestRate / 100 / 12
})

const monthlyPayment = computed(() => {
  const P = amountFinanced.value
  const r = monthlyInterestRate.value
  const n = calculatorForm.value.loanTerm

  if (P <= 0 || r <= 0 || n <= 0) return 0

  // EMI Formula: P × r × (1 + r)^n / ((1 + r)^n - 1)
  const emi = P * r * Math.pow(1 + r, n) / (Math.pow(1 + r, n) - 1)
  return Math.round(emi)
})

const totalPayable = computed(() => {
  return monthlyPayment.value * calculatorForm.value.loanTerm
})

const totalInterest = computed(() => {
  return totalPayable.value - amountFinanced.value
})

const handleLoanApplication = () => {
  console.log('Loan application:', {
    carPrice: calculatorForm.value.carPrice,
    downPayment: downPaymentAmount.value,
    loanTerm: calculatorForm.value.loanTerm,
    interestRate: calculatorForm.value.interestRate,
    monthlyPayment: monthlyPayment.value
  })
  alert(`Thank you for your interest! Our finance team will contact you shortly to discuss loan options for your ৳${formatPrice(calculatorForm.value.carPrice)} car.`)
}

// Tabs for car categories
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

// Cars data - MUST be defined before filteredCars
const cars = ref([
  {
    id: 1,
    name: 'Toyota Corolla Cross',
    type: 'suvs',
    image: 'https://images.unsplash.com/photo-1581540222194-0d38b4d8a7d0?q=80&w=800&auto=format&fit=crop',
  },
  {
    id: 2,
    name: 'Toyota Axio Hybrid',
    type: 'sedans',
    image: 'https://images.unsplash.com/photo-1621007947382-bb3c3994e3fb?q=80&w=800&auto=format&fit=crop',
  },
  {
    id: 3,
    name: 'Toyota Fielder Hybrid',
    type: 'estates',
    image: 'https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?q=80&w=800&auto=format&fit=crop',
  },
  {
    id: 4,
    name: 'Toyota Noah',
    type: 'mpv',
    image: 'https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=800&auto=format&fit=crop',
  },
  {
    id: 5,
    name: 'Toyota Voxy',
    type: 'mpv',
    image: 'https://images.unsplash.com/photo-1549317661-bd32c8ce0db2?q=80&w=800&auto=format&fit=crop',
  },
  {
    id: 6,
    name: 'Honda Vezel Hybrid',
    type: 'suvs',
    image: 'https://images.unsplash.com/photo-1568605117036-5fe5e4ba0f5a?q=80&w=800&auto=format&fit=crop',
  },
  {
    id: 7,
    name: 'Toyota Harrier',
    type: 'suvs',
    image: 'https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?q=80&w=800&auto=format&fit=crop',
  },
  {
    id: 8,
    name: 'Honda Grace Hybrid',
    type: 'sedans',
    image: 'https://images.unsplash.com/photo-1621007947382-bb3c3994e3fb?q=80&w=800&auto=format&fit=crop',
  }
])

// filteredCars - MUST be defined after cars
const filteredCars = computed(() => {
  return cars.value.filter(car => car.type === activeTab.value)
})

// Carousel state
const currentSlide = ref(0)
const slidesPerView = ref(3)

// Auto-slide functionality
let autoSlideInterval = null
const autoSlideDelay = 4000 // 4 seconds

const startAutoSlide = () => {
  if (autoSlideInterval) clearInterval(autoSlideInterval)
  autoSlideInterval = setInterval(() => {
    if (currentSlide.value < maxSlides.value) {
      currentSlide.value++
    } else {
      currentSlide.value = 0
    }
  }, autoSlideDelay)
}

const pauseAutoSlide = () => {
  if (autoSlideInterval) {
    clearInterval(autoSlideInterval)
    autoSlideInterval = null
  }
}

const resumeAutoSlide = () => {
  if (filteredCars.value.length > slidesPerView.value) {
    startAutoSlide()
  }
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

// Update slides per view based on screen size
const updateSlidesPerView = () => {
  if (typeof window !== 'undefined') {
    if (window.innerWidth < 640) {
      slidesPerView.value = 1
    } else if (window.innerWidth < 1024) {
      slidesPerView.value = 2
    } else {
      slidesPerView.value = 3
    }
  }
}

// maxSlides computed - MUST be defined after filteredCars and slidesPerView
const maxSlides = computed(() => Math.max(0, Math.ceil(filteredCars.value.length / slidesPerView.value) - 1))

// Watch for tab changes to restart auto-slide
watch(activeTab, () => {
  currentSlide.value = 0
  pauseAutoSlide()
  setTimeout(() => {
    if (filteredCars.value.length > slidesPerView.value) {
      startAutoSlide()
    }
  }, 100)
})

// Watch for filtered cars change
watch(filteredCars, (newCars) => {
  pauseAutoSlide()
  if (newCars.length > slidesPerView.value) {
    setTimeout(() => startAutoSlide(), 100)
  }
})

onMounted(() => {
  updateSlidesPerView()
  window.addEventListener('resize', updateSlidesPerView)
  if (filteredCars.value.length > slidesPerView.value) {
    startAutoSlide()
  }
})

onUnmounted(() => {
  window.removeEventListener('resize', updateSlidesPerView)
  pauseAutoSlide()
})
</script>