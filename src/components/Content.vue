<script setup lang="ts">
import { ref } from 'vue'
import type { TabsPaneContext } from 'element-plus'
import TabItem from "./TabItem.vue";

const activeName = ref('iPhone 13 Pro')

const handleClick = (tab: TabsPaneContext, event: Event) => {
  console.log(tab, event)
}


const phones = [
  {
    title: "iPhone 13 Pro",
    description: "Искусственный интеллект и технология A16 Bionic обеспечивают превосходную производительность и эффективность энергопотребления. Экран Super Retina XDR предлагает яркий и четкий изображение даже при ярком солнечном свете. Камера Ultra Wide, Wide и Telephoto с поддержкой Night mode позволяет захватывать прекрасные моменты в любых условиях освещенности.",
    price: 9999,
    colors: ['red', 'blue', 'green']
  },
  {
    title: "Samsung Galaxy S21 Ultra",
    description: "Экран Dynamic AMOLED 2X с разрешением WQHD+ и частотой обновления до 120 Гц обеспечивает плавное и яркое изображение. Система камеры с тремя модулями - основной, широкоугольный и сверхширокоугольный - позволяет записывать видео и делать фото высокого качества. Батарея на 5000 мАч обеспечивает долгое время работы без подзарядки.",
    price: 10999,
    colors: ['purple', 'white']
  },
  {
    title: "Google Pixel 6 Pro",
    description: "Камера Google Pixel 6 Pro использует технологию Magic Eraser для удаления нежелательных элементов из фотографий. Процессор Tensor SoC от Google обеспечивает быструю работу устройства и эффективное управление энергией. Экран Fluid AMOLED с частотой обновления до 120 Гц предлагает плавное и яркое изображение. Батарея на 5003 мАч обеспечивает длительное время работы между зарядками.",
    price: 8999,
    colors: ['grey', 'orange', 'blue', 'white']
  },
  {
    title: "Xiaomi Mi 11 Ultra",
    description: "Технология HyperCharge 67W позволяет быстро заряжать устройство до 100% за 23 минуты. Экран Dual Display с диагональю 6,81 дюйма и разрешением WQHD+ обеспечивает яркие и четкие изображения. Камера Leica Triple Camera System включает в себя широкоугольный, сверхширокоугольный и перископический модули, а также фазовый датчик глубины LiDAR для улучшенной фокусации и измерения расстояния.",
    price: 7999,
    colors: ['black', 'pink', 'green', 'orange', 'yellow', 'blue']

  }
];

</script>

<template>
  <el-tabs v-model="activeName" class="demo-tabs" @tab-click="handleClick">
    <el-tab-pane :label="phone.title" :name="phone.title" :key="i" v-for="(phone, i) in phones"><TabItem :phone="phone"/></el-tab-pane>
  </el-tabs>
</template>