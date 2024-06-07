<script setup lang="ts">
import { CheckboxValueType } from 'element-plus';
import { ref } from 'vue';

const availableNomenclaturesArr = [
  'Первая номенклатура',
  'Вторая номенклатура',
  'Третья номенклатура',
  'Четвертая номенклатура',
  'Пятая номенклатура',
  'Шестая номенклатура',
  'Седьмая номенклатура',
  'Восьмая номенклатура',
  'Девятая номенклатура',
  'Десятая номенклатура',
  'Одиннадцатая номенклатура',
  'Двенадцатая номенклатура',
  'Тринадцатая номенклатура',
  'Четырнадцатая номенклатура',
  'Пятнадцатая номенклатура',
  'Шестнадцатая номенклатура',
  'Семнадцатая номенклатура',
  'Восемнадцатая номенклатура',
  'Девятнадцатая номенклатура',
  'Двадцатая номенклатура',
  'Двадцать первая номенклатура',
  'Двадцать вторая номенклатура',
  'Двадцать третья номенклатура',
  'Двадцать четвертая номенклатура',
  'Двадцать пятая номенклатура',
  'Двадцать шестая номенклатура',
  'Двадцать седьмая номенклатура',
  'Двадцать восьмая номенклатура',
  'Двадцать девятая номенклатура',
  'Тридцатая номенклатура',
];

const input1 = ref('');

const checkAllAvailableNomenclatures = ref(false);
const isIndeterminate = ref(true);
const chechedAvailibleNomenclature = ref(['Первая номенклатура', 'Третья номенклатура']);

// если val = true? то присвается весь массив чекнутых, false - [].
const handleCheckAllAvailableNomenclatures = (val: CheckboxValueType) => {
  chechedAvailibleNomenclature.value = val ? availableNomenclaturesArr : [];
  isIndeterminate.value = false;
};

const handlecheckAvailibleNomenclature = (value: CheckboxValueType[]) => {
  const checkedCount = value.length;
  checkAllAvailableNomenclatures.value = checkedCount === availableNomenclaturesArr.length;
  isIndeterminate.value = checkedCount > 0 && checkedCount < availableNomenclaturesArr.length;
};
</script>

<template>
  <div class="grid grid-cols-2 gap-10 px-40 py-10">
    <form class="a-card--outline grid gap-2 p-4 border h-[500px]">
      <h3 class="text-xl">Доступные номеклатуры</h3>
      <el-input v-model="input1" size="large" placeholder="Введите название" />
      <el-checkbox
        v-model="checkAllAvailableNomenclatures"
        class="w-full"
        :indeterminate="isIndeterminate"
        @change="handleCheckAllAvailableNomenclatures"
      >
        <span class="text-lg">Выделить все</span>
      </el-checkbox>
      <el-divider style="margin-top: 5px; margin-bottom: 5px" />
      <el-scrollbar class="max-h-200px">
        <el-checkbox-group
          v-model="chechedAvailibleNomenclature"
          class="grid"
          @change="handlecheckAvailibleNomenclature"
        >
          <el-checkbox v-for="item in availableNomenclaturesArr" :key="item" :label="item" :value="item">
            {{ item }}
          </el-checkbox>
        </el-checkbox-group>
      </el-scrollbar>
      <el-divider style="margin-top: 10px; margin-bottom: 10px"></el-divider>
      <el-button size="large"><span class="text-lg">Добавить выбранное</span></el-button>
    </form>
    <!--     <form class="a-card--outline grid gap-2 p-4 border h-[500px]">
      <h3 class="text-xl">Номенклатуры в комлексе</h3>
      <el-input v-model="input1" size="large" placeholder="Введите название" />
      <el-checkbox v-model="checkAll" class="w-full" :indeterminate="isIndeterminate" @change="handleCheckAllChange">
        <span class="text-lg">Выделить все</span>
      </el-checkbox>
      <el-divider style="margin-top: 5px; margin-bottom: 5px"></el-divider>
      <el-scrollbar class="max-h-200px">
        <el-checkbox-group
          v-model="chechedAvailibleNomenclature"
          class="grid"
          @change="handlechechedAvailibleNomenclatureChange"
        >
          <el-checkbox v-for="item in availableNomenclaturesArr" :key="item" :label="item" :value="item">
            {{ item }}
          </el-checkbox>
        </el-checkbox-group>
      </el-scrollbar>
      <el-divider style="margin-top: 10px; margin-bottom: 10px"></el-divider>
      <el-button size="large" type="danger"><span class="text-lg">Удалить выбранное</span></el-button>
    </form> -->
  </div>
</template>
