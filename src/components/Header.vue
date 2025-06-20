<template>
  <!-- шапка «прилипает» и слегка сжимается при прокрутке -->
  <header
    :class="[
      'fixed top-0 left-1/2 -translate-x-1/2 w-[90%] md:w-[80%] z-50',
      scrolled ? 'scale-95 shadow-xl/30' : 'scale-100 shadow-none',
      'transition-all duration-300 ease-[cubic-bezier(0.4,0,0.2,1)] backdrop-blur-lg',
      'bg-gradient-to-br from-gray-900/80 via-slate-900/70 to-gray-800/80 border border-gray-700/40 rounded-full',
    ]"
  >
    <nav class="flex items-center justify-between px-6 py-3">
      <!-- логотип -->
      <div class="flex items-center space-x-3">
        <div
          class="w-12 h-12 bg-gradient-to-r from-blue-500 to-purple-600 rounded-xl flex items-center justify-center animate-pulse-slow"
        >
          <Sparkles class="w-6 h-6 text-white" />
        </div>
        <span
          class="text-2xl font-extrabold bg-gradient-to-r from-blue-400 via-pink-400 to-purple-400 bg-clip-text text-transparent"
        >
          SolarStudio
        </span>
      </div>

      <!-- навигация -->
      <ul class="hidden lg:flex items-center space-x-8 font-medium">
        <li v-for="link in links" :key="link.to" class="relative group">
          <a
            :href="link.to"
            class="flex items-center gap-2 text-slate-300 hover:text-cyan-400 transition-colors"
          >
            <component :is="link.icon" class="w-5 h-5" />
            {{ link.label }}
          </a>
          <!-- анимированное подчеркивание -->
          <span
            class="absolute left-0 -bottom-1 h-[2px] w-0 bg-gradient-to-r from-cyan-400 to-pink-400 rounded-full group-hover:w-full transition-all duration-300"
          />
        </li>
      </ul>

      <!-- бургер для мобилки -->
      <button
        @click="open = !open"
        class="lg:hidden p-2 rounded-lg hover:bg-white/10 transition"
      >
        <Menu class="w-6 h-6" />
      </button>
    </nav>

    <!-- выпадающее меню на мобилке -->
    <transition name="fade">
      <ul
        v-if="open"
        class="lg:hidden flex flex-col gap-4 px-6 pb-6 pt-2 text-center font-medium"
      >
        <li
          v-for="link in links"
          :key="`m-${link.to}`"
          class="flex items-center justify-center gap-2 text-slate-300 hover:text-cyan-400 transition"
        >
          <component :is="link.icon" class="w-5 h-5" />
          <a :href="link.to">{{ link.label }}</a>
        </li>
      </ul>
    </transition>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import {
  Sparkles,
  Home,
  Image as Gallery,
  Newspaper,
  BadgePercent,
  Info,
  Users,
  Menu,
} from "lucide-vue-next";

const open = ref(false);
const scrolled = ref(false);

const links = [
  { label: "Главная", to: "#home", icon: Home },
  { label: "Портфолио", to: "#portfolio", icon: Gallery },
  { label: "Новости", to: "#news", icon: Newspaper },
  { label: "Подписки", to: "#subscriptions", icon: BadgePercent },
  { label: "О нас", to: "#about", icon: Info },
  { label: "Команда", to: "#team", icon: Users },
];

const onScroll = () => (scrolled.value = window.scrollY > 40);
onMounted(() => window.addEventListener("scroll", onScroll));
onUnmounted(() => window.removeEventListener("scroll", onScroll));
</script>

<style scoped>
@keyframes pulse-slow {
  0%,
  100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
}
.animate-pulse-slow {
  animation: pulse-slow 3s ease-in-out infinite;
}

/* плавное появление мобильного меню */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.25s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
