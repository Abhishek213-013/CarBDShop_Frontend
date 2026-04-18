<template>
  <section class="relative min-h-screen flex items-center z-10 pb-32">
    <div class="container mx-auto relative py-20">
      <div class="max-w-4xl">
        <div class="mb-8 flex items-center gap-3">
          <span class="text-white text-sm font-light tracking-[0.3em] uppercase">Since 2020</span>
          <span class="w-12 h-[1px] bg-primary"></span>
          <span class="text-white text-sm font-light tracking-[0.3em] uppercase">Premium Import</span>
        </div>
        
        <h1 class="text-5xl md:text-7xl lg:text-8xl font-bold text-white mb-6 leading-[1.1]">
          Bangladesh's Premium<br />
          Destination for<br />
          <span class="text-primary">Japanese Cars</span>
        </h1>
        
        <p class="text-lg md:text-xl text-white/80 mb-10 max-w-xl leading-relaxed">
          Direct from Japan Auctions. Fully Verified. Delivered with Confidence.
        </p>
        
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
    
    <div class="absolute bottom-8 left-1/2 -translate-x-1/2 z-10 hidden md:block">
      <div class="flex flex-col items-center gap-2 text-white/50">
        <span class="text-xs uppercase tracking-widest">Scroll</span>
        <div class="w-[1px] h-16 bg-gradient-to-b from-white/50 to-transparent"></div>
      </div>
    </div>
  </section>
</template>