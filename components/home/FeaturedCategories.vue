<template>
  <section class="relative z-10 py-20 bg-white">
    <div class="container mx-auto">
      <div class="text-center mb-12">
        <p class="section-subtitle">Secure Your Car Before Arrival</p>
        <h2 class="section-title">Featured Categories</h2>
        <p class="text-gray-600 max-w-2xl mx-auto">Stock arriving soon - Prebook now to secure your vehicle.</p>
      </div>
      
      <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-4">
        <div v-for="category in categories" :key="category.name" class="text-center p-6 border border-gray-200 hover:border-primary hover:shadow-lg transition-all duration-300 bg-white">
          <h3 class="text-lg font-bold mb-2">{{ category.name }}</h3>
          <p class="text-primary text-sm font-medium mb-3">Stock arriving soon</p>
          <NuxtLink to="/prebook" class="text-dark text-sm font-medium hover:text-primary transition-colors inline-flex items-center gap-1">
            Prebook now →
          </NuxtLink>
        </div>
      </div>
      
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
</template>

<script setup>
const categories = [
  { name: 'Corolla Cross' },
  { name: 'Axio Hybrid' },
  { name: 'Fielder Hybrid' },
  { name: 'Noah / Voxy' },
  { name: 'Premium SUVs' }
]
</script>