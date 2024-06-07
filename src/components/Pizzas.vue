<script setup lang="ts">
import { onMounted, ref } from 'vue';
import Pizza from './Pizza.vue';

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

const pizzas = ref<Pizza[]>([]);

const getPizzas = async () => {
  try {
    const res = await fetch('https://62b53b6eda3017eabb16fb77.mockapi.io/items');
    const pizzas = await res.json();
    return pizzas;
  } catch (err) {
    console.log(err);
  }
};
onMounted(async () => {
  pizzas.value = await getPizzas();
});
</script>

<template>
  <h1
    class="text-3xl inline-flex items-center gap-2 ml-10 mt-10 box-decoration-slice bg-gradient-to-r from-indigo-600 to-pink-500 text-white px-4 py-3 rounded-full"
  >
    <el-icon :size="50"><Orange /></el-icon> Pizza
  </h1>
  <ul class="grid grid-cols-3 gap-10 mx-64 py-20">
    <Pizza :pizzas="pizzas" />
  </ul>
</template>

<style scoped></style>
