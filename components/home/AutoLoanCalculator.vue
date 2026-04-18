<template>
  <section class="relative z-10 py-20">
    <div class="absolute inset-0 z-0">
      <img 
        src="https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=1920&auto=format&fit=crop"
        alt="Luxury Car Finance"
        class="w-full h-full object-cover"
      />
      <div class="absolute inset-0 bg-gradient-to-r from-dark/95 via-dark/85 to-dark/70"></div>
    </div>

    <div class="container mx-auto relative z-10">
      <div class="text-center mb-12">
        <p class="section-subtitle text-primary">Plan Your Purchase</p>
        <h2 class="section-title text-white">Auto Loan Calculator</h2>
        <p class="text-white/70 max-w-2xl mx-auto">Use our calculator to estimate your monthly car payments.</p>
      </div>

      <div class="max-w-4xl mx-auto">
        <div class="bg-dark/40 backdrop-blur-sm border border-white/10 shadow-2xl p-8 md:p-10">
          <div class="mb-8">
            <label class="block text-sm font-semibold text-white/80 mb-2">Total Price</label>
            <div class="flex items-center gap-4">
              <span class="text-3xl font-bold text-primary">৳</span>
              <input 
                type="number" 
                v-model="calculatorForm.carPrice"
                min="0"
                step="50000"
                class="w-full px-4 py-3 text-3xl font-bold border-0 border-b-2 border-white/20 focus:border-primary focus:outline-none bg-transparent text-white placeholder-white/30"
                placeholder="Enter car price"
              />
            </div>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-8">
            <div>
              <div class="flex justify-between items-center mb-2">
                <label class="block text-sm font-semibold text-white/80">Down Payment</label>
                <span class="text-primary font-bold">{{ downPaymentPercentage }}%</span>
              </div>
              <input 
                type="range" 
                v-model="downPaymentPercentage"
                min="0" max="50" step="1"
                class="w-full h-1 bg-white/20 rounded-full appearance-none cursor-pointer [&::-webkit-slider-thumb]:appearance-none [&::-webkit-slider-thumb]:w-5 [&::-webkit-slider-thumb]:h-5 [&::-webkit-slider-thumb]:bg-primary [&::-webkit-slider-thumb]:rounded-full [&::-webkit-slider-thumb]:cursor-pointer [&::-webkit-slider-thumb]:border-2 [&::-webkit-slider-thumb]:border-white [&::-webkit-slider-thumb]:shadow-md"
              />
              <div class="flex justify-between text-xs text-white/50 mt-1">
                <span>0%</span><span>25%</span><span>50%</span>
              </div>
            </div>

            <div>
              <div class="flex justify-between items-center mb-2">
                <label class="block text-sm font-semibold text-white/80">Loan Term</label>
                <span class="text-primary font-bold">{{ calculatorForm.loanTerm }} months</span>
              </div>
              <input 
                type="range" 
                v-model="calculatorForm.loanTerm"
                min="12" max="60" step="12"
                class="w-full h-1 bg-white/20 rounded-full appearance-none cursor-pointer [&::-webkit-slider-thumb]:appearance-none [&::-webkit-slider-thumb]:w-5 [&::-webkit-slider-thumb]:h-5 [&::-webkit-slider-thumb]:bg-primary [&::-webkit-slider-thumb]:rounded-full [&::-webkit-slider-thumb]:cursor-pointer [&::-webkit-slider-thumb]:border-2 [&::-webkit-slider-thumb]:border-white [&::-webkit-slider-thumb]:shadow-md"
              />
              <div class="flex justify-between text-xs text-white/50 mt-1">
                <span>12 mo</span><span>24 mo</span><span>36 mo</span><span>48 mo</span><span>60 mo</span>
              </div>
            </div>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-8">
            <div>
              <div class="flex justify-between items-center mb-2">
                <label class="block text-sm font-semibold text-white/80">Interest Rate</label>
                <span class="text-primary font-bold">{{ calculatorForm.interestRate }}%</span>
              </div>
              <input 
                type="range" 
                v-model="calculatorForm.interestRate"
                min="0" max="15" step="0.5"
                class="w-full h-1 bg-white/20 rounded-full appearance-none cursor-pointer [&::-webkit-slider-thumb]:appearance-none [&::-webkit-slider-thumb]:w-5 [&::-webkit-slider-thumb]:h-5 [&::-webkit-slider-thumb]:bg-primary [&::-webkit-slider-thumb]:rounded-full [&::-webkit-slider-thumb]:cursor-pointer [&::-webkit-slider-thumb]:border-2 [&::-webkit-slider-thumb]:border-white [&::-webkit-slider-thumb]:shadow-md"
              />
              <div class="flex justify-between text-xs text-white/50 mt-1">
                <span>0%</span><span>5%</span><span>10%</span><span>15%</span>
              </div>
            </div>

            <div class="bg-primary/10 border border-primary/30 p-6 backdrop-blur-sm">
              <p class="text-sm text-white/60 mb-2">Monthly Payment</p>
              <p class="text-5xl font-bold text-white">{{ formatPrice(monthlyPayment) }}</p>
              <p class="text-xs text-white/40 mt-2">per month</p>
            </div>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-3 gap-6 pt-6 border-t border-white/10">
            <div>
              <p class="text-xs text-white/50 uppercase tracking-wider mb-1">Down Payment Amount</p>
              <p class="text-2xl font-bold text-white">{{ formatPrice(downPaymentAmount) }}</p>
            </div>
            <div>
              <p class="text-xs text-white/50 uppercase tracking-wider mb-1">Amount Financed</p>
              <p class="text-2xl font-bold text-white">{{ formatPrice(amountFinanced) }}</p>
            </div>
            <div>
              <p class="text-xs text-white/50 uppercase tracking-wider mb-1">Total Interest</p>
              <p class="text-2xl font-bold text-white">{{ formatPrice(totalInterest) }}</p>
            </div>
          </div>

          <div class="flex flex-col md:flex-row items-center justify-between gap-6 mt-10">
            <button 
              @click="handleLoanApplication"
              class="bg-primary text-white px-10 py-4 font-semibold text-sm uppercase tracking-wider hover:bg-white hover:text-dark transition-all duration-300 flex items-center gap-2"
            >
              Apply for a Loan
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
              </svg>
            </button>
            
            <div class="flex items-center gap-3">
              <span class="text-white/40 text-xs uppercase tracking-widest">Powered by</span>
              <span class="text-white text-lg font-bold tracking-wider">AUTO FINANCE</span>
            </div>
          </div>

          <p class="text-center text-xs text-white/30 mt-6">
            * Multiple banks available for comparison. Contact us for personalized loan options.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const calculatorForm = ref({ carPrice: 2500000, loanTerm: 48, interestRate: 9 })
const downPaymentPercentage = ref(20)

const formatPrice = (value) => {
  if (value >= 10000000) return `৳${(value / 10000000).toFixed(2)} Cr`
  if (value >= 100000) return `৳${(value / 100000).toFixed(2)} L`
  return `৳${Math.round(value).toLocaleString()}`
}

const downPaymentAmount = computed(() => (calculatorForm.value.carPrice * downPaymentPercentage.value) / 100)
const amountFinanced = computed(() => calculatorForm.value.carPrice - downPaymentAmount.value)
const monthlyInterestRate = computed(() => calculatorForm.value.interestRate / 100 / 12)

const monthlyPayment = computed(() => {
  const P = amountFinanced.value
  const r = monthlyInterestRate.value
  const n = calculatorForm.value.loanTerm
  if (P <= 0 || r <= 0 || n <= 0) return 0
  return Math.round(P * r * Math.pow(1 + r, n) / (Math.pow(1 + r, n) - 1))
})

const totalPayable = computed(() => monthlyPayment.value * calculatorForm.value.loanTerm)
const totalInterest = computed(() => totalPayable.value - amountFinanced.value)

const handleLoanApplication = () => {
  alert(`Thank you for your interest! Our finance team will contact you shortly to discuss loan options for your ${formatPrice(calculatorForm.value.carPrice)} car.`)
}
</script>