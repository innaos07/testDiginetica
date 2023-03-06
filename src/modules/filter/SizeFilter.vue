<template>
  <fieldset class="filter__item item-filter">
    <div class="filter__size size-filter">
      <header-filter :isActiveInput="isActiveInput">Размер</header-filter>
      
      <checkbox-filter-list
        :checkboxFilterList="sizeList"
        v-model="checkList"
      />
    </div>
  </fieldset>
</template>

<script setup>
import { ref } from "vue";
import HeaderFilter from "./HeaderFilter.vue";
import CheckboxFilterList from "@/modules/filter/CheckboxFilterList.vue";
const isActiveInput = ref(false)

const props = defineProps({
  sizeList: {
    type: Array,
    default: () => [],
  },
});

const checkList = ref([]);
</script>

<style>
</style>