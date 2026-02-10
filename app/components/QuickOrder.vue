<template>
  <div>
    <UiSheet>
      <UiSheetTrigger as-child>
        <UiButton variant="ghost" size="icon-lg">
          <UiChip text="1" size="xl" class="text-white">
            <Icon name="solar:bag-4-broken" />
          </UiChip>
        </UiButton>
      </UiSheetTrigger>

      <UiSheetContent class="sm:max-w-none md:w-[450px] p-2 lg:p-0" side="left" title="سبد خرید"
        description="در این بخش میتوانید سبد خرید خود را ویرایش کنید.">
        <template #content>
          <UiScrollArea dir="rtl" class="h-8/12">
            <div class="flex items-center justify-center">
              <UiList class="max-w-sm">
                <template v-for="n in cartItems" :key="n.product">
                  <div class="flex items-center justify-between">
                    <UiListItem class="items-start px-0">
                      <img :src="`https://avatar.vercel.sh/${n.product}`" class="rounded-2xl w-1/6" />
                      <UiListContent class="gap-5">
                        <UiListTitle :title="n.product" />
                        <UiListSubtitle>
                          <p>تعداد: {{ n.quantity }}</p>
                        </UiListSubtitle>
                        <p class="ml-auto text-sm font-semibold">
                          {{ n.price }} هزار تومان
                        </p>
                      </UiListContent>
                    </UiListItem>
                    <UiTooltip disable-closing-trigger>
                      <template #trigger>
                        <UiTooltipTrigger as-child>

                          <UiButton variant="destructive">
                            <Icon name="solar:close-circle-bold" />
                          </UiButton>
                        </UiTooltipTrigger>
                      </template>
                      <template #content>
                        <UiTooltipContent>
                          <p>حذف</p>
                        </UiTooltipContent>
                      </template>
                    </UiTooltip>
                  </div>
                  <UiSeparator class="my-2 ml-auto w-[85%] last:hidden" />
                </template>
              </UiList>
            </div>
          </UiScrollArea>
        </template>
        <template #footer>
          <UiSheetFooter>
            <div class="flex flex-col gap-3">
              <span>قمیت کل: 1 میلیون تومان</span>
              <UiButton class="dark:text-white" variant="default">پرداخت</UiButton>
              <UiButton class="dark:text-white" variant="outline">سبد خرید</UiButton>
            </div>
          </UiSheetFooter>
        </template>
      </UiSheetContent>
    </UiSheet>
  </div>
</template>

<script lang="ts" setup>
const cartItems = [
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
  { product: "محصول تستی 1", price: 100.000, quantity: 3 },
]
</script>

<style></style>