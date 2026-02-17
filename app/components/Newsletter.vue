<template>
  <Motion initial="initial" in-view="animate" :in-view-options="{ once: true }" as-child :variants="containerVariant">
    <UiContainer class="py-16 lg:py-24 border border-dashed rounded-2xl">
      <div class="mx-auto max-w-2xl text-center">
        <Motion as-child :variants="childVariant">
          <UiBadge variant="secondary" class="mb-4">خبرنامه</UiBadge>
        </Motion>
        <Motion as-child :variants="childVariant">
          <h2 class="mb-4 text-3xl font-bold tracking-tight md:text-4xl lg:text-5xl">
            جدیدترین اخبار سایت رو از همه زودتر مطلع شو!
          </h2>
        </Motion>
        <Motion as-child :variants="childVariant">
          <p class="mb-8 text-lg text-muted-foreground lg:text-xl">
            با عضویت در خبرنامه سایت، از جدیدترین محصولات، تخفیف ها و مقاله ها با خبر شوید.
          </p>
        </Motion>
        <Motion as-child :variants="childVariant">
          <form class="mx-auto flex max-w-md flex-col gap-3 sm:flex-row">
            <UiVeeInput class="flex-1" type="email" required placeholder="ایمیل خود را وارد کنید."
              aria-label="Enter your email" />
            <UiButton type="submit" class="whitespace-nowrap dark:text-white">عضویت</UiButton>
          </form>
        </Motion>
        <Motion as-child :variants="childVariant">
          <p class="mt-4 text-sm text-muted-foreground">
            ایمیل و اطلاعات شما محفوط است.
          </p>
        </Motion>
      </div>
    </UiContainer>
  </Motion>
</template>

<script lang="ts" setup>
import { stagger } from "motion-v";
import type { MotionProps } from "motion-v";

const containerVariant: MotionProps["variants"] = {
  initial: { opacity: 0 },
  animate: {
    opacity: 1,
    transition: {
      when: "beforeChildren",
      delayChildren: stagger(0.1),
    },
  },
};

const childVariant: MotionProps["variants"] = {
  initial: { opacity: 0, y: 20 },
  animate: {
    opacity: 1,
    y: 0,
    transition: {
      type: "spring",
      stiffness: 200,
      damping: 20,
    },
  },
};
</script>
