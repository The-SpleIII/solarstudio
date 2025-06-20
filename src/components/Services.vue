<template>
  <section id="services" class="py-20 px-6 bg-gray-900/30 backdrop-blur-sm">
    <div class="container mx-auto text-center mb-16">
      <h2
        class="text-4xl md:text-5xl font-bold mb-6 bg-gradient-to-r from-purple-400 to-blue-400 bg-clip-text text-transparent"
      >
        Наши услуги
      </h2>
      <p class="text-xl text-gray-300 max-w-3xl mx-auto">
        Индивидуальные решения под ваши задачи
      </p>
    </div>
    <div class="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
      <div
        v-for="(s, i) in services"
        :key="i"
        class="group bg-gray-900/80 p-8 rounded-2xl transition hover:scale-105 cursor-pointer"
      >
        <div
          :class="`w-16 h-16 bg-gradient-to-r ${s.color} rounded-2xl flex items-center justify-center mb-6`"
        >
          <component :is="s.icon" class="w-8 h-8 text-white" />
        </div>
        <h3 class="text-xl font-bold mb-3 text-white">{{ s.title }}</h3>
        <p class="text-gray-400 text-sm mb-6 leading-relaxed">{{ s.desc }}</p>
        <p
          :class="`text-2xl font-bold bg-gradient-to-r ${s.color} bg-clip-text text-transparent mb-4`"
        >
          {{ s.price }}
        </p>
        <button
          class="w-full py-3 rounded-xl text-white"
          :class="`bg-gradient-to-r ${s.color}`"
        >
          Заказать
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";
import {
  Globe,
  Sparkles,
  Zap,
  Orbit,
  ShoppingCart,
  Star,
} from "lucide-vue-next";

const services = ref([
  {
    icon: Globe,
    title: "Веб-разработка",
    desc: "Современные сайты и приложения с адаптивным дизайном",
    price: "от 15,000₽",
    color: "from-cyan-500 to-blue-500",
  },
  {
    icon: Sparkles,
    title: "UI/UX Дизайн",
    desc: "Интуитивные интерфейсы и пользовательский опыт",
    price: "от 10,000₽",
    color: "from-pink-500 to-purple-500",
  },
  {
    icon: Zap,
    title: "Брендинг",
    desc: "Создание уникальной идентичности бренда",
    price: "от 20,000₽",
    color: "from-emerald-500 to-green-500",
  },
  {
    icon: Orbit,
    title: "Консалтинг",
    desc: "Стратегические решения для вашего бизнеса",
    price: "от 5,000₽",
    color: "from-orange-500 to-red-500",
  },
  {
    icon: ShoppingCart,
    title: "E-commerce",
    desc: "Интернет-магазины с полной интеграцией",
    price: "от 40,000₽",
    color: "from-purple-500 to-pink-500",
  },
  {
    icon: Star,
    title: "SEO продвижение",
    desc: "Оптимизация и продвижение в поисковых системах",
    price: "от 8,000₽",
    color: "from-yellow-500 to-orange-500",
  },
]);
</script>
