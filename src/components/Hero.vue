<template>
  <section
    id="home"
    ref="heroRef"
    class="relative flex items-center justify-center min-h-screen px-6 text-center"
  >
    <div>
      <!-- мини-плашка -->
      <div
        class="inline-flex items-center gap-2 bg-gradient-to-r from-cyan-600/20 to-purple-600/20 backdrop-blur-sm px-5 py-1.5 rounded-full mb-6"
      >
        <Star class="w-4 h-4 text-yellow-400" />
        <span class="text-xs tracking-wide uppercase">
          Решения для Minecraft
        </span>
      </div>

      <!-- заголовок -->
      <h1
        class="text-5xl sm:text-6xl md:text-7xl font-extrabold mb-6 leading-tight bg-gradient-to-r from-cyan-300 via-pink-300 to-emerald-300 bg-clip-text text-transparent animate-glow"
      >
        SolarStudio
      </h1>

      <!-- подзаголовок -->
      <p class="text-lg md:text-xl text-gray-300 mb-10 max-w-2xl mx-auto">
        Студия по&nbsp;созданию и&nbsp;полной настройке
        <b>Minecraft-серверов</b>. Проектируем плагины, подбираем сборки,
        настраиваем экономику, дизайн&nbsp;и маркетинг — всё
        <i>“под&nbsp;ключ”</i>.
      </p>

      <!-- кнопки -->
      <div class="flex flex-col sm:flex-row gap-3 justify-center">
        <button
          @click="$emit('open-products')"
          class="bg-gradient-to-r from-cyan-500 to-pink-500 hover:from-cyan-600 hover:to-pink-600 text-white px-8 py-3 rounded-full text-base font-semibold shadow-lg hover:scale-105 transition-all duration-300"
        >
          Услуги
          <Server class="inline-block w-4 h-4 ml-2" />
        </button>

        <button
          class="border border-white/40 bg-white/10 hover:bg-white hover:text-gray-900 text-white px-8 py-3 rounded-full text-base font-semibold transition-all duration-300"
        >
          Портфолио
          <Eye class="inline-block w-4 h-4 ml-2" />
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { Star, Server, Eye } from "lucide-vue-next";

const heroRef = ref(null);

// параллакс-сдвиг
onMounted(() => {
  window.addEventListener("scroll", () => {
    if (heroRef.value)
      heroRef.value.style.transform = `translateY(${window.scrollY * -0.4}px)`;
  });
});
</script>

<style scoped>
@keyframes glow {
  0%,
  100% {
    text-shadow: 0 0 18px rgba(34, 211, 238, 0.4);
  }
  50% {
    text-shadow: 0 0 30px rgba(34, 211, 238, 0.7),
      0 0 35px rgba(236, 72, 153, 0.6), 0 0 40px rgba(16, 185, 129, 0.5);
  }
}
.animate-glow {
  animation: glow 3s ease-in-out infinite;
}
</style>
