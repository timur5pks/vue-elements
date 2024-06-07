<script setup lang="ts">

import {ref} from "vue";

interface Phone {
  title: string;
  description: string;
  price: number;
  colors: string[],
}

defineProps<{
  phone: Phone
}>();

const value = ref('')

</script>

<template>
  <div class="grid grid-cols-3 gap-3">
    <p class="col-start-2">{{phone.description}}</p>
    <span class="col-start-2">{{phone.price}} Р.</span>
    <el-select v-model="value" placeholder="Выберите цвет" class="col-span col-start-2">
      <el-option 
          v-for="(color, i) in phone.colors" 
          :key="i"
          :label="color"
          :value="color"/>
    </el-select>
    <el-date-picker
        class="col-start-2"
        type="datetime"
        placeholder="Выберите дату и время"
    />
    <el-button type="primary" class="w-20 col-start-2 justify-self-end">Купить</el-button>
  </div>
</template>

<style scoped>

</style>