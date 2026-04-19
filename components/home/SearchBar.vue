<template>
  <section class="relative z-20 -mt-20 pb-8">
    <div class="container mx-auto">
      <div class="bg-white shadow-2xl max-w-6xl mx-auto">
        <form @submit.prevent="handleSearch" class="p-8">
          <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-6">
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
          
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6 items-end">
            <!-- Price Range with Dual Slider -->
            <div>
              <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">PRICE RANGE</label>
              <div class="flex items-center gap-4 mb-2">
                <span class="text-dark font-semibold">{{ formatPrice(minPrice) }}</span>
                <span class="text-gray-400">-</span>
                <span class="text-dark font-semibold">{{ formatPrice(maxPrice) }}</span>
              </div>
              
              <!-- Dual Range Slider -->
              <div class="mt-4 px-2">
                <div class="relative h-1 bg-gray-200 rounded-full">
                  <!-- Active Track Fill -->
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
                    :value="minPrice"
                    @input="handleMinPriceInput"
                    :min="0" 
                    :max="MAX_PRICE" 
                    step="50000"
                    class="price-slider price-slider-min"
                  />
                  
                  <!-- Max Price Slider -->
                  <input 
                    type="range"
                    :value="maxPrice"
                    @input="handleMaxPriceInput"
                    :min="0" 
                    :max="MAX_PRICE" 
                    step="50000"
                    class="price-slider price-slider-max"
                  />
                </div>
                
                <!-- Price Labels -->
                <div class="flex justify-between text-xs text-gray-500 mt-2">
                  <span>৳0</span>
                  <span>৳25L</span>
                  <span>৳50L</span>
                  <span>৳75L</span>
                  <span>৳1Cr</span>
                </div>
              </div>
            </div>
            
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
</template>

<script setup>
import { ref, watch } from 'vue'

const searchForm = ref({
  make: '',
  model: '',
  bodyStyle: ''
})

const MAX_PRICE = 10000000 // 1 Crore
const minPrice = ref(0)
const maxPrice = ref(MAX_PRICE)

// Handle min price input with validation
const handleMinPriceInput = (event) => {
  const value = parseInt(event.target.value)
  if (value <= maxPrice.value) {
    minPrice.value = value
  } else {
    minPrice.value = maxPrice.value
  }
}

// Handle max price input with validation
const handleMaxPriceInput = (event) => {
  const value = parseInt(event.target.value)
  if (value >= minPrice.value) {
    maxPrice.value = value
  } else {
    maxPrice.value = minPrice.value
  }
}

// Watch for cross-validation
watch(minPrice, (newVal) => {
  if (newVal > maxPrice.value) {
    maxPrice.value = newVal
  }
})

watch(maxPrice, (newVal) => {
  if (newVal < minPrice.value) {
    minPrice.value = newVal
  }
})

const formatPrice = (value) => {
  if (value >= 10000000) return `৳${(value / 10000000).toFixed(2)} Cr`
  if (value >= 100000) return `৳${(value / 100000).toFixed(2)} L`
  return `৳${Math.round(value).toLocaleString()}`
}

const handleSearch = () => {
  navigateTo({
    path: '/stock',
    query: {
      ...searchForm.value,
      minPrice: minPrice.value,
      maxPrice: maxPrice.value
    }
  })
}
</script>

<style scoped>
/* Price Range Slider Styles */
.price-slider {
  @apply absolute w-full appearance-none bg-transparent pointer-events-none;
  top: -6px;
  height: 24px;
}

.price-slider-min {
  @apply z-20;
}

.price-slider-max {
  @apply z-10;
}

.price-slider::-webkit-slider-thumb {
  @apply appearance-none w-5 h-5 bg-primary rounded-full pointer-events-auto cursor-pointer border-2 border-white shadow-md relative;
}

.price-slider::-moz-range-thumb {
  @apply w-5 h-5 bg-primary rounded-full pointer-events-auto cursor-pointer border-2 border-white shadow-md;
}

.price-slider::-webkit-slider-runnable-track {
  @apply h-1 bg-transparent;
}

.price-slider::-moz-range-track {
  @apply h-1 bg-transparent;
}
</style>