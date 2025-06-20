<template>
  <section id="products" class="py-20 px-6">
    <div class="container mx-auto text-center mb-16">
      <h2
        class="text-4xl md:text-5xl font-bold mb-6 bg-gradient-to-r from-cyan-400 to-pink-400 bg-clip-text text-transparent"
      >
        Наши товары
      </h2>
      <p class="text-xl text-gray-300 max-w-3xl mx-auto">
        Готовые решения для вашего бизнеса
      </p>
    </div>

    <div class="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
      <ProductCard
        v-for="prod in products"
        :key="prod.id"
        :product="prod"
        @select="$emit('select', prod)"
      />
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";
import ProductCard from "./ProductCard.vue";

const products = ref([
  {
    id: 1,
    title: "SolarEasyGrief V4",
    price: "от 2,500₽",
    gradient: "from-cyan-500 to-blue-500",
    icon: "🎮",
    preview: "/img/solareasy_preview.png",
    short:
      "Готовая гриф-сборка: оптимизированные плагины, защита, кастомные предметы и полная настройка «из коробки».",
    details: {
      name: "SolarEasyGrief V4",
      image: "/img/solareasygrief.png",
      compatibility: "Minecraft 1.16.5",
      mode: "Grief",
      dependencies: "Java 17+",
      releaseDate: "19.06.2025",
      buildVersion: "1.3.4",
      pluginsCount: 32,
      support: "1 месяц",
      purchases: 1247,
      rating: 4.8,
      prices: {
        fullWithoutLicense: "5,000₽",
        fullWithLicense: "2,500₽",
        perPlugin: "от 200₽",
      },
      description:
        "Наша сборка Minecraft — это тщательно настроенный игровой клиент, созданный для максимального комфорта и удовольствия. В ней собраны только необходимые моды, плагины и оптимизации…",
      features: [
        "Оптимизированные моды и плагины",
        "Уникальные механики и предметы",
        "Улучшенная генерация мира",
        "Защита от читеров",
        "Работает «из коробки»",
        "Поддержка PlaceholderAPI, Vault и др.",
      ],
      requirements: [
        "Java 17 или выше",
        "Minecraft 1.16.5 (Paper/Spigot)",
        "Минимум 2–4 ГБ ОЗУ",
        "Выделенный хостинг рекомендуется",
      ],
      plugins: [
        "EssentialsX/2.19.7 — базовые команды",
        "WorldEdit/7.2.15 — редактирование мира",
        "WorldGuard/7.0.7 — защита территорий",
        "LuckPerms/5.4.102 — система прав",
        "Vault/1.7.3 — API для экономики",
      ],
    },
  },
  {
    id: 2,
    title: "Лендинг Премиум",
    price: "от 25,000₽",
    gradient: "from-pink-500 to-purple-500",
    icon: "🌐",
  },
  {
    id: 3,
    title: "Интернет-магазин",
    price: "от 50,000₽",
    gradient: "from-emerald-500 to-green-500",
    icon: "🛒",
  },
  {
    id: 4,
    title: "Мобильное приложение",
    price: "от 80,000₽",
    gradient: "from-orange-500 to-red-500",
    icon: "📱",
  },
  {
    id: 5,
    title: "CRM система",
    price: "от 60,000₽",
    gradient: "from-purple-500 to-pink-500",
    icon: "⚡",
  },
  {
    id: 6,
    title: "Брендинг пакет",
    price: "от 30,000₽",
    gradient: "from-blue-500 to-cyan-500",
    icon: "🎨",
  },
]);
</script>
