<template>
  <section id="reviews" class="py-20 px-6">
    <div class="container mx-auto text-center mb-14">
      <h2
        class="text-4xl md:text-5xl font-bold mb-6 bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent"
      >
        Что говорят о нас наши клиенты
      </h2>
    </div>

    <!-- СЛАЙДЕР -->
    <div class="relative mx-auto" :style="{ width: sliderWidth + 'px' }">
      <!-- стрелка влево -->
      <button
        @click="move(-1)"
        class="absolute -left-8 top-1/2 -translate-y-1/2 p-3 rounded-full bg-white/10 hover:bg-white/20 backdrop-blur-sm"
      >
        ‹
      </button>

      <!-- трек -->
      <div
        ref="track"
        class="flex gap-6 overflow-hidden scroll-smooth"
        :style="{ width: sliderWidth + 'px' }"
      >
        <ReviewCard v-for="r in reviews" :key="r.id" :review="r" />
      </div>

      <!-- стрелка вправо -->
      <button
        @click="move(1)"
        class="absolute -right-8 top-1/2 -translate-y-1/2 p-3 rounded-full bg-white/10 hover:bg-white/20 backdrop-blur-sm"
      >
        ›
      </button>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";
import ReviewCard from "./ReviewCard.vue";

/* данные */
const reviews = [
  {
    id: 1,
    name: "Алексей Петров",
    rating: 5,
    text: "Невероятная работа! SolarStudio создали для нас сайт мечты. Всё выполнено на высшем уровне.",
  },
  {
    id: 2,
    name: "Мария Сидорова",
    rating: 5,
    text: "Профессиональный подход и креативные решения. Рекомендую всем!",
  },
  {
    id: 3,
    name: "Дмитрий Козлов",
    rating: 5,
    text: "Отличная команда! Проект выполнили в срок и превзошли все ожидания.",
  },
  {
    id: 4,
    name: "Анна Волкова",
    rating: 4,
    text: "Качественная работа и внимание к деталям. Очень довольны результатом!",
  },
  {
    id: 5,
    name: "Игорь Смирнов",
    rating: 5,
    text: "SolarStudio — это будущее веб-разработки! Инновационные решения и стиль.",
  },
  {
    id: 6,
    name: "Николай Ершов",
    rating: 5,
    text: "Поддержка реагирует мгновенно. Всё решается за минуту!",
  },
  {
    id: 7,
    name: "Виктория Орлова",
    rating: 4,
    text: "Красивый дизайн, удобная админка. Мелочи быстро поправили.",
  },
  {
    id: 8,
    name: "Сергей Лебедев",
    rating: 5,
    text: "Запустил сервер за вечер. Доход вырос вдвое — класс!",
  },
  {
    id: 9,
    name: "Елена Михайлова",
    rating: 5,
    text: "Сделали лендинг, конверсия 12 %. Спасибо!",
  },
];

/* размеры */
const CARD = 256; // ширина карточки
const GAP = 24; // gap между ними
const SHOW = 5; // сколько видно
const sliderWidth = CARD * SHOW + GAP * (SHOW - 1);

/* прокрутка */
const track = ref(null);
let idx = 0;
function move(dir) {
  const max = reviews.length - SHOW;
  idx = Math.min(Math.max(idx + dir, 0), max);
  track.value?.scrollTo({
    left: idx * (CARD + GAP),
    behavior: "smooth",
  });
}
</script>

<style scoped>
/* убираем системный скролл */
div[ref="track"]::-webkit-scrollbar {
  display: none;
}
div[ref="track"] {
  scrollbar-width: none;
}
</style>
