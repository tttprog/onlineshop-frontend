<template>
  <div class="flex flex-col gap-5 mb-5">
    <Hero />
    <!-- TODO trust options -->
    <!--  best sugesstions -->
    <UiContainer>
      <div class="h-130 bg-blue-800 rounded-2xl flex flex-col gap-3 px-5 py-3">
        <div class="flex gap-5 items-center justify-between">
          <div class="flex items-center gap-3">
            <img src="/images/persent.png" alt="best suggestions!" class="bg-cover animate-bounce hidden lg:flex">
            <strong class="lg:text-2xl text-white">پیشنهاد شگفت انگیز!</strong>
          </div>
          <UiButton variant="outline" icon="solar:arrow-left-broken" icon-placement="right" to="#">مشاهده
            همه
          </UiButton>
        </div>
        <UiDivider />
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
      <div class="grid grid-cols-2 lg:grid-cols-4 gap-5">
        <div class="h-60 rounded-2xl" v-for="(_, index) in 4">
          <NuxtLink to="#">
            <img src="/images/logo.jpg" alt="title"
              class="rounded-2xl hover:scale-105 transition-all duration-300 h-full w-f">
          </NuxtLink>
        </div>
      </div>
    </UiContainer>
    <!-- categories -->
    <div class="bg-gray-100 dark:bg-gray-900 py-5">
      <UiContainer>
        <div class="h-full flex flex-col gap-5 items-center justify-center my-10">
          <strong class="font-bold text-xl">دسته بندی ها</strong>
          <div class="grid grid-cols-2 lg:grid-cols-7 gap-5 justify-center items-center">
            <NuxtLink :to="category.href" class="flex flex-col items-center gap-5"
              v-for="(category, index) in categoris">
              <img :src="category.skin" :alt="category.name"
                class="rounded-full h-32 w-32 hover:scale-110 transition-all duration-300"
                :title="category.description">
              <span class="font-bold">{{ category?.name }}</span>
            </NuxtLink>
          </div>
        </div>
      </UiContainer>
    </div>
    <UiContainer>
      <div class="h-130 bg-orange-500 dark:bg-orange-700 rounded-2xl flex flex-col gap-3 px-5 py-3">
        <div class="flex gap-5 items-center justify-between">
          <div class="flex items-center gap-3">
            <img src="/images/persent.png" alt="best suggestions!" class="bg-cover animate-bounce hidden lg:flex">
            <strong class="lg:text-2xl text-white">محبوب ترین محصولات</strong>
          </div>
          <UiButton variant="outline" icon="solar:arrow-left-broken" icon-placement="right" to="#">مشاهده
            همه
          </UiButton>
        </div>
        <UiDivider />
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
    <UiContainer>
      <div class="grid grid-cols-1 lg:grid-cols-2 items-center gap-5 justify-items-normal">
        <div class="h-80 rounded-2xl" v-for="(_, index) in 2">
          <NuxtLink to="#">
            <img src="/images/logo.jpg" alt="title" class="rounded-2xl h-full w-full">
          </NuxtLink>
        </div>
      </div>
    </UiContainer>
    <UiContainer>
      <div class="h-130 bg-indigo-500 dark:bg-indigo-700 rounded-2xl flex flex-col gap-3 px-5 py-3">
        <div class="flex gap-5 items-center justify-between">
          <div class="flex items-center gap-3">
            <img src="/images/persent.png" alt="best suggestions!" class="bg-cover animate-bounce hidden lg:flex">
            <strong class="lg:text-2xl text-white">جدید ترین محصولات</strong>
          </div>
          <UiButton variant="outline" icon="solar:arrow-left-broken" icon-placement="right" to="#">مشاهده
            همه
          </UiButton>
        </div>
        <UiDivider />

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

    <!-- TODO latest articles -->
    <!-- TODO join news -->
    <!-- TODO footer -->


  </div>

</template>

<script lang="ts" setup>
import Autoplay from "embla-carousel-autoplay";

const categoris = [
  {
    name: "مراقبت از پوست",
    description: "کرم‌های مراقبتی، سرم‌ها و محصولات پوستی",
    skin: "/images/skin.svg",
    slug: "skin-care",
    href: "/category/skin-care",
  },
  {
    name: "مراقبت از مو",
    description: "شامپو، ماسک مو، سرم و محصولات تقویت مو",
    skin: "/images/hair.svg",
    slug: "hair-care",
    href: "/category/hair-care",
  },
  {
    name: "محصولات بهداشتی",
    description: "محصولات بهداشت فردی و روزانه",
    skin: "/images/personal-care.jpg",
    slug: "personal-care",
    href: "/category/personal-care",
  },
  {
    name: "لوازم آرایش صورت",
    description: "انواع کرم پودر، کانسیلر، پنکیک و محصولات آرایش صورت",
    skin: "/images/face-makeup.png",
    slug: "face-makeup",
    href: "/category/face-makeup",
  },
  {
    name: "آرایش چشم و ابرو",
    description: "ریمل، خط چشم، سایه چشم و محصولات ابرو",
    skin: "/images/eye-makeup.jpg",
    slug: "eye-makeup",
    href: "/category/eye-makeup",
  },
  {
    name: "آرایش لب",
    description: "رژ لب، برق لب، خط لب و بالم لب",
    skin: "/images/lip-makeup.jpg",
    slug: "lip-makeup",
    href: "/category/lip-makeup",
  },
  {
    name: "ابزار آرایشی",
    description: "براش، اسفنج، آینه و ابزار تخصصی آرایش",
    skin: "/images/makeup-tools.jpg",
    slug: "makeup-tools",
    href: "/category/makeup-tools",
  },

]

</script>

<style></style>