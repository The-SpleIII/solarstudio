<template>
  <footer
    class="py-12 px-6 border-t border-gray-800/50 bg-black/60 backdrop-blur-sm"
  >
    <div class="container mx-auto grid md:grid-cols-4 gap-8 mb-8">
      <div>
        <div class="flex items-center space-x-2 mb-4">
          <Sparkles class="w-5 h-5 text-white" />
          <span
            class="text-xl font-bold bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent"
            >SolarStudio</span
          >
        </div>
        <p class="text-gray-400 text-sm">
          Создаем будущее сегодня. Инновационные решения для вашего бизнеса.
        </p>
      </div>
      <div>
        <h3 class="text-lg font-bold mb-4 text-white">Контакты</h3>
        <p class="text-gray-400 text-sm">hello@solarstudio.space</p>
        <p class="text-gray-400 text-sm">+7 (999) 123-45-67</p>
        <p class="text-gray-400 text-sm">Москва, Космическая ул., 42</p>
      </div>
      <div>
        <h3 class="text-lg font-bold mb-4 text-white">Услуги</h3>
        <p class="text-gray-400 text-sm">Веб-разработка</p>
        <p class="text-gray-400 text-sm">UI/UX Дизайн</p>
        <p class="text-gray-400 text-sm">Брендинг</p>
        <p class="text-gray-400 text-sm">Консалтинг</p>
      </div>
      <div>
        <h3 class="text-lg font-bold mb-4 text-white">Соцсети</h3>
        <div class="flex space-x-4">
          <InstagramIcon class="w-5 h-5" />
          <TwitterIcon class="w-5 h-5" />
          <FacebookIcon class="w-5 h-5" />
          <YoutubeIcon class="w-5 h-5" />
          <LinkedinIcon class="w-5 h-5" />
        </div>
      </div>
    </div>
    <div class="text-center text-gray-400 text-sm">
      © 2024 SolarStudio. Все права защищены.
    </div>
  </footer>
</template>

<script setup>
import {
  Sparkles,
  Instagram as InstagramIcon,
  Twitter as TwitterIcon,
  Facebook as FacebookIcon,
  Youtube as YoutubeIcon,
  Linkedin as LinkedinIcon,
} from "lucide-vue-next";
</script>
