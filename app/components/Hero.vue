<script setup lang="ts">
// Create 10 slides
const containerRef = ref(null)
const slides = ref(Array.from({ length: 8 }))


const swiper = useSwiper(containerRef, {
  effect: "creative",
  loop: true,
  autoplay: {
    delay: 1000,
  }
})

onMounted(() => {
  console.log(swiper.instance)
})
</script>

<template>
  <ClientOnly>
    <swiper-container ref="containerRef">
      <swiper-slide v-for="(slide, idx) in slides" :key="idx" style="background-color: rgb(32, 233, 70); color: white;">
        Slide {{ idx + 1 }}
      </swiper-slide>
    </swiper-container>
  </ClientOnly>
</template>

<style lang="css">
swiper-slide {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 18px;
  height: 40vh;
  font-size: 4rem;
  font-weight: bold;
  font-family: 'Roboto', sans-serif;
}
</style>
