<template>
  <section class="relative z-10 py-20 bg-gray-50">
    <div class="container mx-auto">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
        <div>
          <p class="section-subtitle">Making Car Import Safe & Transparent</p>
          <h2 class="section-title">About CarBDShop</h2>
          <p class="text-gray-600 mb-6 leading-relaxed">
            We source vehicles directly from Japanese auctions, focusing exclusively on high-quality vehicles with verified auction grades (Grade 4 / 4.5 / 5). Every vehicle comes with complete transparency in pricing, inspection reports, and the entire import process.
          </p>
          <p class="text-gray-600 mb-8 leading-relaxed">
            Our mission is simple: <span class="font-semibold text-dark">Making car import safe, transparent, and premium.</span>
          </p>
          
          <div class="grid grid-cols-2 gap-4">
            <div v-for="point in keyPoints" :key="point" class="flex items-center gap-3">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
              </svg>
              <span class="text-dark font-medium">{{ point }}</span>
            </div>
          </div>
        </div>
        
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
</template>

<script setup>
const keyPoints = ['Grade 4/4.5/5 Only', 'Full Transparency', 'Auction Verified', 'Premium Service']
</script>