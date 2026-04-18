<template>
  <section class="relative z-10 py-20 bg-gray-50">
    <div class="container mx-auto">
      <div class="text-center mb-12">
        <p class="section-subtitle">Real Deliveries, Real Customers</p>
        <h2 class="section-title">Social Proof</h2>
        <p class="text-gray-600 max-w-2xl mx-auto">See what our customers say about their CarBDShop experience.</p>
      </div>
      
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
        <div v-for="(item, index) in galleryItems" :key="index" class="relative group overflow-hidden">
          <img :src="item.image" :alt="item.label" class="w-full h-48 object-cover group-hover:scale-105 transition-transform duration-500" />
          <div class="absolute inset-0 bg-dark/50 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
            <span class="text-white font-medium">{{ item.label }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const galleryItems = [
  { image: 'https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=400&auto=format&fit=crop', label: 'Delivery Photo' },
  { image: 'https://images.unsplash.com/photo-1581540222194-0d38b4d8a7d0?q=80&w=400&auto=format&fit=crop', label: 'Inspection Video' },
  { image: 'https://images.unsplash.com/photo-1568605117036-5fe5e4ba0f5a?q=80&w=400&auto=format&fit=crop', label: 'Showroom' },
  { image: 'https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?q=80&w=400&auto=format&fit=crop', label: 'Happy Customer' }
]
</script>