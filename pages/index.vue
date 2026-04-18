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
        <img 
          src="https://images.unsplash.com/photo-1580273916550-e323be2ae537?q=80&w=1920&auto=format&fit=crop"
          alt="Luxury Japanese Car"
          class="w-full h-full object-cover"
        />
      </video>
      <div class="absolute inset-0 bg-gradient-to-r from-black/80 via-black/50 to-transparent"></div>
    </div>

    <HomeHeroSection />
    <HomeSearchBar />
    <HomeTrustStrip />
    <HomeOurModels />
    <HomeAboutSection />
    <HomeHowItWorks />
    <HomeWhyChooseUs />
    <HomePrebookTradeinForms />
    <HomeAutoLoanCalculator />
    <HomeFeaturedCategories />
    <HomeBlogPreview />
    <HomeContactShowroom />
    <HomeSocialProof />
  </div>
</template>

<script setup>
// No logic needed here - all handled in components
</script>