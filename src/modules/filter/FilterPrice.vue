<template>
  <fieldset class="filter__item item-filter">
    <div class="filter__price price-filter">
      <header-filter :isActiveInput="isActiveInput">Цена</header-filter>

      <div class="price-filter__range">
        <div class="price-filter__input price-filter__input--min">
          <input
            type="text"
            name="minPrice"
            placeholder="5 500 ₽"
            v-model="minPrice"
          />
        </div>
        <span class="price-filter__elem"></span>
        <div class="price-filter__input price-filter__input--max">
          <input
            type="text"
            name="maxPrice"
            placeholder="5 500 ₽"
            v-model="maxPrice"
          />
        </div>
      </div>
    </div>
  </fieldset>
</template>

<script setup>
import { ref } from "vue";
import HeaderFilter from "./HeaderFilter.vue";
const minPrice = ref("");
const maxPrice = ref("");
const isActiveInput = ref(false);
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";

.price-filter {
  .price-filter__range {
    position: relative;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .price-filter__elem {
    width: 10px;
    height: 1px;
    background: $color-border;
  }

  .price-filter__input {
    position: relative;
    &::before {
      position: absolute;
      display: flex;
      align-items: center;
      justify-content: center;

      width: 12px;
      height: 14px;
      font-size: 12px;
      line-height: 117%;
      color: $color-font-second;
    }

    &--min::before {
      content: "от";
      top: 11px;
      left: 8px;
    }

    &--max::before {
      content: "до";
      top: 11px;
      left: 8px;
    }

    input {
      width: 119px;
      padding: 10px 8px;
      padding-left: 26px;
      border: 1px solid $color-border;
      border-radius: 4px;

      &:hover,
      &:focus {
        outline: none;
        border-color: $color-brand;
        transition: all 0.5s;
      }
    }
  }
}
</style>