<template>
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
        <div v-for="(step, index) in steps" :key="index" class="text-center group">
          <div class="w-20 h-20 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4 group-hover:bg-primary transition-all duration-300">
            <span class="text-primary text-2xl font-bold group-hover:text-white">{{ index + 1 }}</span>
          </div>
          <h3 class="text-xl font-bold mb-3">{{ step.title }}</h3>
          <p class="text-gray-600">{{ step.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const steps = [
  { title: 'Choose / Prebook', description: 'Select from upcoming inventory or request a custom car tailored to your needs.' },
  { title: 'Auction Verification', description: 'We provide auction sheet, grade, and complete inspection details for transparency.' },
  { title: 'Secure & Ship', description: 'We handle the purchase, shipping, and complete import process for you.' },
  { title: 'Delivery & Support', description: 'Receive your vehicle with complete documentation and ongoing support.' }
]
</script>