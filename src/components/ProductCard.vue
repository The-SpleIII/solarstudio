<template>
  <div
    @click="$emit('select', product)"
    class="group w-72 rounded-2xl overflow-hidden bg-gray-900/80 border border-gray-800/60 hover:border-cyan-500/50 shadow-lg/40 transition hover:scale-[1.04] cursor-pointer"
  >
    <!-- БАННЕР -->
    <div class="relative h-44 w-full overflow-hidden">
      <img
        :src="product.preview"
        :alt="product.title"
        class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
      />
      <!-- фиолетово-синий оверлей для единого стиля -->
      <div
        class="absolute inset-0 bg-gradient-to-b from-purple-700/30 via-indigo-700/20 to-transparent"
      />
    </div>

    <!-- КОНТЕНТ -->
    <div class="p-5 space-y-3">
      <!-- заголовок + цена -->
      <div class="flex items-center justify-between">
        <h3 class="text-base font-bold text-white truncate pr-2">
          {{ product.title }}
        </h3>
        <span
          :class="`px-3 py-0.5 rounded-full text-xs font-bold text-white shadow bg-gradient-to-r ${product.gradient}`"
        >
          {{ product.price }}
        </span>
      </div>

      <!-- краткое описание -->
      <p class="text-sm text-gray-300 leading-snug line-clamp-2">
        {{ product.short || "Описание скоро будет" }}
      </p>

      <!-- кнопка -->
      <button
        class="block w-full py-2.5 rounded-lg text-sm font-semibold text-white bg-gradient-to-r from-cyan-500 to-pink-500 hover:from-cyan-600 hover:to-pink-600 transition"
      >
        Подробнее
      </button>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
defineProps({ product: Object });
</script>

<style scoped>
/* если нет плагина @tailwindcss/line-clamp, замените .line-clamp-2 на .truncate */
</style>
