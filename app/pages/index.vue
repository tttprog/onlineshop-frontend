<template>
  <div class="flex flex-col gap-5">
    <Hero />
    <!--  best sugesstions -->
    <UiContainer>
      <div class="h-120 bg-blue-800 rounded-2xl flex flex-col gap-3 px-5 py-3">
        <div class="flex gap-5 items-center justify-between">
          <div class="flex items-center gap-3">
            <img src="/images/persent.png" alt="best suggestions!" class="bg-cover animate-bounce">
            <strong class="lg:text-2xl text-white">پیشنهاد شگفت انگیز!</strong>
          </div>
          <UiButton variant="outline" icon="solar:arrow-left-broken" icon-placement="right" to="#">مشاهده
            همه
          </UiButton>
        </div>
        <div class="h-full flex items-center justify-center">
          <UiCarousel class="relative w-full" :opts="{ align: 'start', direction: 'rtl', loop: true }"
            :plugins="[Autoplay({ delay: 2000 })]">
            <UiCarouselContent>
              <UiCarouselItem v-for="(_, index) in 10" :key="index" grab-cursor class="md:basis-1/2 lg:basis-1/5">
                <div class="p-1">
                  <UiCard>
                    <UiCardContent class="flex aspect-square items-center justify-center p-6">
                      <span class="text-3xl font-semibold">{{ index + 1 }}</span>
                    </UiCardContent>
                  </UiCard>
                </div>
              </UiCarouselItem>
            </UiCarouselContent>
          </UiCarousel>
        </div>
      </div>
    </UiContainer>
    <!-- banners -->
    <UiContainer>
      <div class="grid grid-cols-2 lg:grid-cols-4">
        <div class="h-60 bg-red-500 border gap-10" v-for="(_, index) in 4">dsfg</div>
      </div>
    </UiContainer>
  </div>
</template>

<script lang="ts" setup>
import Autoplay from "embla-carousel-autoplay";

</script>

<style></style>