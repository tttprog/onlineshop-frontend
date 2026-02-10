<template>
  <header class="z-20 border-b bg-background/90 backdrop-blur">
    <UiAlert icon="solar:danger-circle-broken" variant="warning" description="اعلان عمومی" icon-class="mt-0.5" />
    <UiContainer class="flex h-16 items-center justify-between lg:h-20">
      <div class="flex items-center gap-10">
        <NuxtLink to="/" class="flex items-center gap-3">
          <img src="/images/logo.jpg" fit="contain" alt="Logo" title="Logo" class="h-6 rounded object-contain lg:h-8" />
          <span class="font-semibold lg:text-lg">آنلاین شاپ آلمان</span>
        </NuxtLink>
      </div>
      <div class="lg:hidden gap-3 flex items-center">
        <UiButton size="icon" variant="ghost" @click="changeColorMode">
          <Icon class="size-4" :name="colorMode.value === 'dark' ? 'solar:sun-2-broken' : 'solar:moon-broken'" />
        </UiButton>
        <QuickOrder />
        <UiSheet>
          <UiSheetTrigger as-child>
            <UiButton variant="ghost" size="icon-sm">
              <Icon name="lucide:menu" class="h-5 w-5" />
            </UiButton>
            <UiSheetContent class="w-[90%] p-0 text-end" side="right">
              <template #content>
                <UiSheetTitle class="sr-only" title="Mobile menu" />
                <UiSheetDescription class="sr-only" description="Mobile menu" />
                <UiSheetX class="z-20" />

                <UiScrollArea class="h-full p-5 text-right">
                  <div class="flex flex-col gap-2" dir="rtl">
                    <UiButton variant="ghost" class="justify-start text-base" to="#">خانه</UiButton>
                    <template v-for="(data, link, i) in links" :key="i">
                      <UiCollapsible>
                        <UiCollapsibleTrigger as-child>
                          <UiButton variant="ghost"
                            class="w-full justify-start text-base capitalize *:data-[state=open]:-rotate-180" to="#">{{
                              link }}
                            <Icon name="lucide:chevron-down" class="ml-auto size-4 transition" />
                          </UiButton>
                        </UiCollapsibleTrigger>
                        <UiCollapsibleContent
                          class="data-[state=closed]:animate-none data-[state=open]:p-3 data-[state=open]:pt-0 bg-gray-100 dark:bg-black dark:border">
                          <div v-for="(item, cat, index) in data" :key="`${cat}-${index}`" class="mt-5">
                            <p class="mb-5 text-sm font-semibold text-primary capitalize">
                              {{ cat }}
                            </p>
                            <ul class="flex w-full flex-col gap-2">
                              <li v-for="(child, k) in item" :key="k">
                                <UiNavigationMenuLink class="data-active:bg-muted/80" as-child>
                                  <NuxtLink :to="child.href"
                                    class="flex flex-row gap-4 rounded-md p-3 transition hover:bg-muted/80 focus-visible:ring-2 focus-visible:ring-ring/50 focus-visible:outline-none">
                                    <Icon :name="child.icon" class="mt-px h-5 w-5 shrink-0 text-primary" />
                                    <div class="flex flex-col gap-1.5 leading-none">
                                      <p class="text-sm font-semibold">{{ child.name }}</p>
                                    </div>
                                  </NuxtLink>
                                </UiNavigationMenuLink>
                              </li>
                            </ul>
                          </div>
                        </UiCollapsibleContent>
                      </UiCollapsible>
                    </template>
                    <UiButton to="#" class="justify-start text-base" variant="ghost" size="sm">درباره ما</UiButton>
                    <UiButton to="#" class="justify-start text-base" variant="ghost" size="sm">تماس با ما</UiButton>

                    <UiGradientDivider class="my-5" />

                    <UiButton to="#" class="dark:text-white">ثبت نام</UiButton>
                    <UiButton variant="outline" to="#" class="mb-52">ورود</UiButton>
                  </div>
                </UiScrollArea>
              </template>
            </UiSheetContent>
          </UiSheetTrigger>
        </UiSheet>

      </div>
      <div class="hidden lg:flex">

        <UiNavigationMenu as="nav" class="hidden items-center justify-start gap-8 lg:flex">
          <UiNavigationMenuList class="gap-2 flex-row-reverse">
            <UiNavigationMenuItem>
              <UiNavigationMenuLink as-child>
                <UiButton to="/" variant="ghost" size="sm"> خانه</UiButton>
              </UiNavigationMenuLink>
            </UiNavigationMenuItem>
            <template v-for="(data, link, i) in links" :key="i">
              <UiNavigationMenuItem>
                <UiNavigationMenuTrigger class="h-9 px-3 text-sm capitalize" :title="link" />
                <UiNavigationMenuContent>
                  <div class="grid grid-cols-1 gap-5 p-4 lg:w-[650px] lg:grid-cols-2" dir="rtl">
                    <div v-for="(item, cat, index) in data" :key="`${cat}-${index}`">
                      <p class="mb-5 text-sm font-semibold text-primary capitalize">{{ cat }}</p>
                      <ul class="flex w-full flex-col gap-2">
                        <li v-for="(child, k) in item" :key="k">
                          <UiNavigationMenuLink class="data-active:bg-muted/80" as-child>
                            <NuxtLink :to="child.href"
                              class="flex flex-row gap-4 rounded-md p-3 transition hover:bg-muted/80 focus-visible:ring-2 focus-visible:ring-ring/50 focus-visible:outline-none">
                              <Icon :name="child.icon" class="mt-px h-5 w-5 shrink-0 text-primary" />
                              <div class="flex flex-col gap-1.5 leading-none">
                                <p class="text-sm font-semibold">{{ child.name }}</p>
                                <p class="text-sm text-muted-foreground" v-html="child.description" />
                              </div>
                            </NuxtLink>
                          </UiNavigationMenuLink>
                        </li>
                      </ul>
                    </div>
                  </div>
                </UiNavigationMenuContent>
              </UiNavigationMenuItem>
            </template>
            <UiNavigationMenuItem>
              <UiNavigationMenuLink as-child>
                <UiButton to="#" variant="ghost" size="sm">درباره ما</UiButton>
              </UiNavigationMenuLink>
            </UiNavigationMenuItem>
            <UiNavigationMenuItem>
              <UiNavigationMenuLink as-child>
                <UiButton to="#" variant="ghost" size="sm">تماس با ما</UiButton>
              </UiNavigationMenuLink>
            </UiNavigationMenuItem>
          </UiNavigationMenuList>
        </UiNavigationMenu>
      </div>
      <div class="hidden items-center gap-3 lg:flex">
        <QuickOrder />
        <UiButton size="icon" variant="ghost" @click="changeColorMode">
          <Icon class="size-4" :name="colorMode.value === 'dark' ? 'solar:sun-2-broken' : 'solar:moon-broken'" />
        </UiButton>
        <UiButton to="#" variant="outline" size="sm">ورود</UiButton>
        <UiButton to="#" size="sm" class="dark:text-white">ثبت نام</UiButton>
      </div>
    </UiContainer>
  </header>
</template>

<script lang="ts" setup>
const categories = {
  "دسته بندی": {
    "زیبایی و آرایشی": [
      {
        name: "لوازم آرایش صورت",
        description: "انواع کرم پودر، کانسیلر، پنکیک و محصولات آرایش صورت",
        icon: "lucide:palette",
        slug: "face-makeup",
        href: "/category/face-makeup",
      },
      {
        name: "آرایش چشم و ابرو",
        description: "ریمل، خط چشم، سایه چشم و محصولات ابرو",
        icon: "lucide:eye",
        slug: "eye-makeup",
        href: "/category/eye-makeup",
      },
      {
        name: "آرایش لب",
        description: "رژ لب، برق لب، خط لب و بالم لب",
        icon: "lucide:smile",
        slug: "lip-makeup",
        href: "/category/lip-makeup",
      },
      {
        name: "ابزار آرایشی",
        description: "براش، اسفنج، آینه و ابزار تخصصی آرایش",
        icon: "lucide:brush",
        slug: "makeup-tools",
        href: "/category/makeup-tools",
      },
    ],

    "مراقبت پوست و مو": [
      {
        name: "مراقبت از پوست",
        description: "کرم‌های مراقبتی، سرم‌ها و محصولات پوستی",
        icon: "lucide:droplet",
        slug: "skin-care",
        href: "/category/skin-care",
      },
      {
        name: "مراقبت از مو",
        description: "شامپو، ماسک مو، سرم و محصولات تقویت مو",
        icon: "lucide:scissors",
        slug: "hair-care",
        href: "/category/hair-care",
      },
      {
        name: "محصولات بهداشتی",
        description: "محصولات بهداشت فردی و روزانه",
        icon: "lucide:shield-check",
        slug: "personal-care",
        href: "/category/personal-care",
      },
    ],

  }
}
const brands = {
  "برندها": [
    {
      name: "لورآل",
      description: "محصولات اورجینال برند L'Oréal",
      icon: "lucide:badge-check",
      slug: "loreal",
      href: "/brand/loreal",
    },
    {
      name: "میبلین",
      description: "محصولات آرایشی برند Maybelline",
      icon: "lucide:star",
      slug: "maybelline",
      href: "/brand/maybelline",
    },
    {
      name: "نوتروژینا",
      description: "محصولات تخصصی مراقبت پوست",
      icon: "lucide:leaf",
      slug: "neutrogena",
      href: "/brand/neutrogena",
    },
  ],
}

const extraLinks = {
  "راهنمای خرید": [
    {
      name: "راهنمای انتخاب محصول",
      description: "کمک به انتخاب بهترین محصول متناسب با نیاز شما",
      icon: "lucide:help-circle",
      slug: "buying-guide",
      href: "/guide/buying",
    },
    {
      name: "سوالات متداول",
      description: "پاسخ به سوالات پرتکرار مشتریان",
      icon: "lucide:message-circle",
      slug: "faq",
      href: "/faq",
    },
    {
      name: "تماس با پشتیبانی",
      description: "ارتباط مستقیم با تیم پشتیبانی فروشگاه",
      icon: "lucide:headphones",
      slug: "support",
      href: "/support",
    },
  ],
}

const links = computed(() => ({
  "دسته بندی": {
    ...categories["دسته بندی"],
    "برند ها": brands["برندها"],
    "راهنمای خرید": extraLinks["راهنمای خرید"],
  },
}))

const colorMode = useColorMode()

const changeColorMode = () => colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark'

</script>
