<template>
  <div
    class="w-60 snap-center flex-shrink-0 p-5 rounded-2xl bg-gray-900/80 backdrop-blur-md border border-gray-800/60 hover:border-cyan-400/50 transition shadow-lg/40 relative"
  >
    <!-- неоновый блик внутри карточки -->
    <div
      class="absolute -right-16 -top-16 w-40 h-40 bg-gradient-to-br from-fuchsia-600/40 to-purple-600/20 rounded-full blur-2xl pointer-events-none"
    />

    <!-- аватар-логотип -->
    <div
      class="w-11 h-11 mb-4 rounded-xl bg-gradient-to-r from-cyan-500 to-purple-500 flex items-center justify-center"
    >
      <Sparkles class="w-5 h-5 text-white" />
    </div>

    <!-- имя -->
    <h3 class="text-sm font-semibold text-white mb-1 truncate">
      {{ review.name }}
    </h3>

    <!-- звёзды -->
    <div class="flex gap-0.5 mb-3">
      <Star
        v-for="n in 5"
        :key="n"
        class="w-4 h-4"
        :class="
          n <= review.rating ? 'text-yellow-400 fill-current' : 'text-white/25'
        "
      />
    </div>

    <!-- текст -->
    <p class="text-xs text-gray-300 leading-snug line-clamp-4">
      {{ review.text }}
    </p>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
import { Star, Sparkles } from "lucide-vue-next";
defineProps({ review: Object });
</script>
