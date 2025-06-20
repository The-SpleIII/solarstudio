<template>
  <div
    class="fixed inset-0 bg-black/80 backdrop-blur-sm z-50 flex items-center justify-center p-4"
  >
    <div
      class="bg-gray-900/95 backdrop-blur-sm border border-gray-800/50 rounded-2xl max-w-5xl w-full max-h-[90vh] overflow-y-auto"
    >
      <!-- Заголовок с кнопкой закрыть -->
      <div
        class="sticky top-0 bg-gray-900/95 backdrop-blur-sm border-b border-gray-800/50 p-6 flex justify-between items-center"
      >
        <div class="flex items-center space-x-4">
          <div
            class="w-12 h-12 rounded-xl flex items-center justify-center text-2xl"
            :class="`bg-gradient-to-r ${product.gradient}`"
          >
            {{ product.icon }}
          </div>
          <div>
            <h2
              class="text-3xl font-bold bg-gradient-to-r from-cyan-400 to-blue-400 bg-clip-text text-transparent"
            >
              {{ product.details.name }}
            </h2>
            <div class="flex items-center space-x-4 mt-1">
              <span class="text-sm text-gray-400"
                >Версия {{ product.details.buildVersion }}</span
              >
              <div class="flex items-center space-x-1">
                <Star
                  v-for="n in 5"
                  :key="n"
                  class="w-4 h-4"
                  :class="
                    n <= Math.floor(product.details.rating)
                      ? 'text-yellow-400 fill-current'
                      : 'text-gray-600'
                  "
                />
                <span class="text-sm text-gray-400 ml-2">{{
                  product.details.rating
                }}</span>
              </div>
              <span class="text-sm text-gray-400"
                >{{ product.details.purchases }} покупок</span
              >
            </div>
          </div>
        </div>
        <button
          @click="$emit('close')"
          class="bg-gray-800/50 hover:bg-gray-700/50 p-2 rounded-full text-white text-xl"
        >
          ✕
        </button>
      </div>

      <!-- Контент модалки -->
      <div class="p-6 space-y-8 text-gray-300">
        <!-- БАННЕР -->
        <div class="relative h-85 w-full overflow-hidden rounded-2xl">
          <img
            :src="product.details.image"
            :alt="product.details.name"
            class="w-full h-full object-cover transition-transform duration-500"
          />
          <div
            :class="`absolute inset-0 bg-gradient-to-r ${product.gradient} opacity-20 pointer-events-none`"
          />
        </div>

        <!-- Технические характеристики и цены -->
        <div class="grid md:grid-cols-2 gap-6">
          <!-- Характеристики -->
          <div class="bg-gray-800/50 rounded-lg p-4">
            <h3 class="text-lg font-bold mb-3 text-cyan-400">
              Технические характеристики
            </h3>
            <div class="space-y-2 text-sm">
              <div class="flex justify-between">
                <span class="text-gray-400">Совместимость:</span
                ><span class="text-white">{{
                  product.details.compatibility
                }}</span>
              </div>
              <div class="flex justify-between">
                <span class="text-gray-400">Режим:</span
                ><span class="text-white">{{ product.details.mode }}</span>
              </div>
              <div class="flex justify-between">
                <span class="text-gray-400">Зависимости:</span
                ><span class="text-white">{{
                  product.details.dependencies
                }}</span>
              </div>
              <div class="flex justify-between">
                <span class="text-gray-400">Дата выпуска:</span
                ><span class="text-white">{{
                  product.details.releaseDate
                }}</span>
              </div>
              <div class="flex justify-between">
                <span class="text-gray-400">Версия сборки:</span
                ><span class="text-white">{{
                  product.details.buildVersion
                }}</span>
              </div>
              <div class="flex justify-between">
                <span class="text-gray-400">Количество плагинов:</span
                ><span class="text-white">{{
                  product.details.pluginsCount
                }}</span>
              </div>
              <div class="flex justify-between">
                <span class="text-gray-400">Техподдержка:</span
                ><span class="text-white">{{ product.details.support }}</span>
              </div>
            </div>
          </div>
          <!-- Цены -->
          <div class="bg-gray-800/50 rounded-lg p-4">
            <h3 class="text-lg font-bold mb-3 text-pink-400">Цены</h3>
            <div class="space-y-3 text-sm">
              <div
                class="bg-gradient-to-r from-cyan-500/20 to-blue-500/20 rounded-lg p-3 border border-cyan-500/30"
              >
                <div class="flex justify-between items-center">
                  <span class="text-white font-medium"
                    >Полная версия без лицензии</span
                  >
                  <span class="text-2xl font-bold text-cyan-400">{{
                    product.details.prices.fullWithoutLicense
                  }}</span>
                </div>
              </div>
              <div
                class="bg-gradient-to-r from-pink-500/20 to-purple-500/20 rounded-lg p-3 border border-pink-500/30"
              >
                <div class="flex justify-between items-center">
                  <span class="text-white font-medium"
                    >Полная версия с лицензией</span
                  >
                  <span class="text-2xl font-bold text-pink-400">{{
                    product.details.prices.fullWithLicense
                  }}</span>
                </div>
                <div class="text-xs text-gray-400 mt-1">
                  Рекомендуемый вариант
                </div>
              </div>
              <div
                class="bg-gradient-to-r from-emerald-500/20 to-green-500/20 rounded-lg p-3 border border-emerald-500/30"
              >
                <div class="flex justify-between items-center">
                  <span class="text-white font-medium"
                    >Цена за плагин из сборки</span
                  >
                  <span class="text-xl font-bold text-emerald-400">{{
                    product.details.prices.perPlugin
                  }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Описание -->
        <div class="bg-gray-800/50 rounded-lg p-6">
          <h3 class="text-xl font-bold mb-4 text-purple-400">Описание</h3>
          <p class="leading-relaxed">{{ product.details.description }}</p>
        </div>

        <!-- Что внутри -->
        <div class="bg-gray-800/50 rounded-lg p-6">
          <h3 class="text-xl font-bold mb-4 text-emerald-400">Что внутри</h3>
          <div class="grid md:grid-cols-2 gap-3">
            <div
              v-for="(feat, idx) in product.details.features"
              :key="idx"
              class="flex items-start space-x-3"
            >
              <div class="w-2 h-2 bg-emerald-400 rounded-full mt-2"></div>
              <span class="text-sm">{{ feat }}</span>
            </div>
          </div>
        </div>

        <!-- Системные требования -->
        <div class="bg-gray-800/50 rounded-lg p-6">
          <h3 class="text-xl font-bold mb-4 text-orange-400">
            Системные требования
          </h3>
          <div class="grid md:grid-cols-2 gap-3">
            <div
              v-for="(req, idx) in product.details.requirements"
              :key="idx"
              class="flex items-start space-x-3"
            >
              <div class="w-2 h-2 bg-orange-400 rounded-full mt-2"></div>
              <span class="text-sm">{{ req }}</span>
            </div>
          </div>
        </div>

        <!-- Список плагинов -->
        <div class="bg-gray-800/50 rounded-lg p-6">
          <h3 class="text-xl font-bold mb-4 text-blue-400">
            Основные плагины (5 из {{ product.details.pluginsCount }})
          </h3>
          <div class="space-y-3">
            <div
              v-for="(plugin, idx) in product.details.plugins.slice(0, 5)"
              :key="idx"
              class="bg-gray-700/50 rounded-lg p-3 border-l-4 border-blue-400"
            >
              <span class="text-sm">{{ plugin }}</span>
            </div>
          </div>
          <div class="mt-4 text-center text-gray-400 text-sm">
            + ещё {{ product.details.pluginsCount - 5 }} плагинов в полной
            версии
          </div>
        </div>

        <!-- Кнопки действий -->
        <div
          class="flex flex-col sm:flex-row gap-4 pt-6 border-t border-gray-800/50"
        >
          <button
            class="flex-1 bg-gradient-to-r from-cyan-500 to-pink-500 hover:from-cyan-600 hover:to-pink-600 text-white py-4 text-lg font-semibold rounded-xl"
          >
            Купить сейчас
          </button>
          <button
            class="flex-1 bg-gradient-to-r from-purple-500 to-blue-500 hover:from-purple-600 hover:to-blue-600 text-white py-4 text-lg font-semibold rounded-xl"
          >
            Видео обзор
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
import { Star } from "lucide-vue-next";

const props = defineProps({
  product: Object,
});
</script>
