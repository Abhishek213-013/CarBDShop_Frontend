<template>
  <section class="relative z-10 py-20 bg-white">
    <div class="container mx-auto">
      <div class="text-center mb-12">
        <p class="section-subtitle">Get Started Today</p>
        <h2 class="section-title">Pre-Book or Trade-In</h2>
        <p class="text-gray-600 max-w-2xl mx-auto">
          Secure your dream car before it arrives or trade in your current vehicle for a great deal.
        </p>
      </div>

      <div class="max-w-5xl mx-auto">
        <div class="flex justify-center gap-4 mb-8">
          <button 
            @click="activeForm = 'prebook'"
            class="px-8 py-4 font-semibold text-sm uppercase tracking-wider transition-all duration-300 flex items-center gap-2"
            :class="activeForm === 'prebook' ? 'bg-primary text-white' : 'bg-gray-100 text-dark hover:bg-gray-200'"
          >
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
            </svg>
            PRE-BOOK A CAR
          </button>
          <button 
            @click="activeForm = 'tradein'"
            class="px-8 py-4 font-semibold text-sm uppercase tracking-wider transition-all duration-300 flex items-center gap-2"
            :class="activeForm === 'tradein' ? 'bg-primary text-white' : 'bg-gray-100 text-dark hover:bg-gray-200'"
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
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Full Name *</label>
                <input type="text" v-model="prebookForm.fullName" required placeholder="Enter your full name" class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark" />
              </div>
              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Phone Number *</label>
                <input type="tel" v-model="prebookForm.phone" required placeholder="Enter your phone number" class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark" />
              </div>
              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Email Address *</label>
                <input type="email" v-model="prebookForm.email" required placeholder="Enter your email" class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark" />
              </div>
              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Preferred Car Model *</label>
                <select v-model="prebookForm.carModel" required class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark">
                  <option value="">Select Model</option>
                  <option value="corolla-cross">Toyota Corolla Cross</option>
                  <option value="axio-hybrid">Toyota Axio Hybrid</option>
                  <option value="fielder-hybrid">Toyota Fielder Hybrid</option>
                  <option value="noah">Toyota Noah</option>
                  <option value="voxy">Toyota Voxy</option>
                  <option value="harrier">Toyota Harrier</option>
                  <option value="premium-suv">Premium SUV</option>
                  <option value="other">Other</option>
                </select>
              </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Preferred Budget Range</label>
                <select v-model="prebookForm.budget" class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark">
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
                <select v-model="prebookForm.timeline" class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark">
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
              <textarea v-model="prebookForm.message" rows="4" placeholder="Any specific requirements or questions..." class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark resize-none"></textarea>
            </div>

            <div class="flex items-center gap-3">
              <input type="checkbox" v-model="prebookForm.agreement" required class="w-4 h-4 text-primary border-gray-300 focus:ring-primary" />
              <label class="text-sm text-gray-600">I agree to be contacted by CarBDShop regarding my pre-booking inquiry.</label>
            </div>

            <div class="flex justify-end pt-4">
              <button type="submit" class="bg-dark text-white px-10 py-4 font-semibold text-sm uppercase tracking-wider hover:bg-primary transition-all duration-300 flex items-center gap-2">
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
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Full Name *</label>
                <input type="text" v-model="tradeinForm.fullName" required placeholder="Enter your full name" class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark" />
              </div>
              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Phone Number *</label>
                <input type="tel" v-model="tradeinForm.phone" required placeholder="Enter your phone number" class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark" />
              </div>
            </div>

            <h4 class="text-lg font-bold text-dark pt-4">Vehicle Details</h4>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Car Model *</label>
                <input type="text" v-model="tradeinForm.carModel" required placeholder="e.g., Toyota Axio" class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark" />
              </div>
              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Registration Year *</label>
                <select v-model="tradeinForm.year" required class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark">
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
                <input type="number" v-model="tradeinForm.mileage" required placeholder="Enter mileage" class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark" />
              </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Asking Price (BDT) *</label>
                <input type="number" v-model="tradeinForm.askingPrice" required placeholder="Enter your asking price" class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark" />
              </div>
              <div class="form-group">
                <label class="block text-xs font-semibold uppercase tracking-wider text-gray-500 mb-2">Condition</label>
                <select v-model="tradeinForm.condition" class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark">
                  <option value="">Select Condition</option>
                  <option value="excellent">Excellent</option>
                  <option value="good">Good</option>
                  <option value="fair">Fair</option>
                  <option value="needs-work">Needs Work</option>
                </select>
              </div>
            </div>

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
              <textarea v-model="tradeinForm.notes" rows="3" placeholder="Any additional information about your vehicle..." class="w-full px-4 py-3 border border-gray-200 focus:border-primary focus:outline-none bg-white text-dark resize-none"></textarea>
            </div>

            <div class="bg-gray-50 p-4 border border-gray-200 flex items-center gap-4">
              <div class="flex items-center gap-2">
                <input type="checkbox" required class="w-4 h-4 text-primary" />
                <span class="text-sm text-gray-600">I'm not a robot</span>
              </div>
              <div class="text-xs text-gray-400">reCAPTCHA</div>
            </div>

            <div class="flex justify-end pt-4">
              <button type="submit" class="bg-dark text-white px-10 py-4 font-semibold text-sm uppercase tracking-wider hover:bg-primary transition-all duration-300 flex items-center gap-2">
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
</template>

<script setup>
import { ref } from 'vue'

const activeForm = ref('prebook')

const prebookForm = ref({
  fullName: '', phone: '', email: '', carModel: '', budget: '', timeline: '', message: '', agreement: false
})

const tradeinForm = ref({
  fullName: '', phone: '', carModel: '', year: '', mileage: '', askingPrice: '', condition: '', notes: ''
})

const handlePrebookSubmit = () => {
  console.log('Pre-booking form submitted:', prebookForm.value)
  prebookForm.value = { fullName: '', phone: '', email: '', carModel: '', budget: '', timeline: '', message: '', agreement: false }
  alert('Thank you for your pre-booking request! We will contact you shortly.')
}

const handleTradeinSubmit = () => {
  console.log('Trade-in form submitted:', tradeinForm.value)
  tradeinForm.value = { fullName: '', phone: '', carModel: '', year: '', mileage: '', askingPrice: '', condition: '', notes: '' }
  alert('Thank you for your trade-in request! We will contact you shortly to request vehicle images.')
}
</script>