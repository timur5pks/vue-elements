<script setup lang="ts">
import { ShoppingCart } from '@element-plus/icons-vue';
import { ref } from 'vue';

interface Pizza {
  id: string;
  imageUrl: string;
  title: string;
  types: number[];
  sizes: number[];
  price: number;
  category: number;
  rating: number;
}

interface PizzasProps {
  pizzas: Pizza[];
}

const props = defineProps<PizzasProps>();

const visibledDialog = ref(false);
const selectedPizza = ref<Pizza>();

const handlePopup = (id: string) => {
  const pizza = props.pizzas.find((pizza) => pizza.id === id);
  if (pizza) {
    // Здесь можно было бы установить выбранную пиццу в состояние, если это необходимо
    selectedPizza.value = pizza;
    visibledDialog.value = true; // Отображаем диалоговое окно
  }
};

const value = ref('');
</script>

<template>
  <li
    v-for="pizza in props.pizzas"
    key="pizza.id"
    class="grid grid-cols-2 gap-y-4 box-decoration-slice bg-gradient-to-r from-indigo-600 to-pink-500 text-white p-6 rounded-3xl"
  >
    <img :src="pizza.imageUrl" :alt="pizza.title" class="col-span-full" />
    <h1 class="text-2xl col-span-full">{{ pizza.title }}</h1>
    <span class="col-start-1 self-center">{{ pizza.price }} Р</span>
    <el-button
      class="col-start-2"
      type="success"
      round
      size="large"
      :icon="ShoppingCart"
      @click="() => handlePopup(pizza.id)"
      >Выбрать</el-button
    >
  </li>
  <el-dialog v-model="visibledDialog" width="400" style="border-radius: 20px; padding: 40px">
    <div class="grid grid-cols-2 gap-3">
      <img :src="selectedPizza?.imageUrl" :alt="selectedPizza?.title" class="col-span-full" />
      <h2 class="text-2xl col-span-full">{{ selectedPizza?.title }}</h2>
      <el-select v-model="value" placeholder="Размер">
        <el-option v-for="(size, i) in selectedPizza?.sizes" :key="i" :value="size" :label="size"> </el-option>
      </el-select>
      <el-select v-model="value" placeholder="Размер">
        <el-option v-for="(size, i) in selectedPizza?.sizes" :key="i" :value="size" :label="size"> </el-option>
      </el-select>
      <span>{{ selectedPizza?.sizes }}</span>
      <span>{{ selectedPizza?.types }}</span>
      <span class="text-2xl col-start-1 self-end">{{ selectedPizza?.price }} Р.</span>
      <el-button type="success" round size="large" :icon="ShoppingCart" class="col-start-2">Добавить</el-button>
    </div>
  </el-dialog>
</template>

<style scoped></style>
