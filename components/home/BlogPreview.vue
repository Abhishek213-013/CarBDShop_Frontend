<template>
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
        <div v-for="post in blogPosts" :key="post.id" class="bg-white shadow-sm hover:shadow-lg transition-all duration-300 border border-gray-100">
          <div class="overflow-hidden bg-gray-100">
            <img 
              :src="post.image" 
              :alt="post.title" 
              @error="handleImageError"
              class="w-full h-48 object-cover hover:scale-105 transition-transform duration-500" 
            />
          </div>
          <div class="p-6">
            <div class="flex items-center gap-4 text-sm text-gray-500 mb-3">
              <span class="bg-primary/10 text-primary px-2 py-1 text-xs font-semibold uppercase">{{ post.category }}</span>
              <span>{{ post.date }}</span>
            </div>
            <h3 class="text-lg font-bold mb-3 hover:text-primary transition-colors">
              <NuxtLink :to="`/blog/${post.id}`">{{ post.title }}</NuxtLink>
            </h3>
            <p class="text-gray-600 text-sm mb-4">{{ post.excerpt }}</p>
            <NuxtLink :to="`/blog/${post.id}`" class="text-primary font-medium hover:text-dark transition-colors inline-flex items-center gap-1">
              Read More →
            </NuxtLink>
          </div>
        </div>
      </div>

      <!-- Empty State - if no blog posts -->
      <div v-if="blogPosts.length === 0" class="text-center py-12">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-16 w-16 text-gray-300 mx-auto mb-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19 20H5a2 2 0 01-2-2V6a2 2 0 012-2h10a2 2 0 012 2v1M5 6h14" />
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 17a2 2 0 11-4 0 2 2 0 014 0zM19 17a2 2 0 11-4 0 2 2 0 014 0z" />
        </svg>
        <p class="text-gray-500 text-lg">Coming Soon</p>
        <p class="text-gray-400 text-sm mt-2">New articles are on the way. Check back soon!</p>
      </div>
    </div>
  </section>
</template>

<script setup>
// Default placeholder image for blog posts
const DEFAULT_BLOG_IMAGE = 'https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=600&auto=format&fit=crop'

const blogPosts = ref([
  { 
    id: 1, 
    title: 'Complete Guide to Japanese Car Auctions', 
    category: 'Guides', 
    date: 'Oct 16, 2024', 
    excerpt: 'Learn how Japanese car auctions work and how to get the best deals on quality vehicles.', 
    image: 'https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=600&auto=format&fit=crop' 
  },
  { 
    id: 2, 
    title: 'Bangladesh Car Import Process Explained', 
    category: 'Import', 
    date: 'Oct 14, 2024', 
    excerpt: 'Step-by-step breakdown of importing a car from Japan to Bangladesh.', 
    image: 'images/imported.jpg' 
  },
  { 
    id: 3, 
    title: 'EMI Calculator: Plan Your Car Purchase', 
    category: 'Finance', 
    date: 'Oct 10, 2024', 
    excerpt: 'Use our EMI calculator to plan your finances and find the best loan options.', 
    image: '/images/blog-image.png'
  }
])

// Handle image error - replace with default
const handleImageError = (event) => {
  event.target.src = DEFAULT_BLOG_IMAGE
}
</script>