<template>
  <a 
    href="#" 
    v-if="quantity" 
    class="item-catalog__btn btn"> 
    Купить 
  </a>
  <button 
    v-else 
    class="item-catalog__btn item-catalog__btn--empty btn"
  >
    Сообщить о поступлении
  </button>
</template>

<script setup>
const props = defineProps({
  quantity: {
    type: Number,
    default: 0,
  },
});
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";

.item-catalog__btn {
  padding: 12px 16px;
  border: 1px solid $color-brand;
  border-radius: 4px;
  background-color: $color-white;
  color: $color-brand;
  cursor: pointer;

  &--empty {
    width: 100%;
    margin-top: 46px;
    border: 1px solid $color-font-second;
    color: $color-font-second;
  }

  &:hover:not(.item-catalog__btn--empty),
  &:focus:not(.item-catalog__btn--empty) {
    background-color: $color-brand;
    color: $color-white;
    transition: all 0.5s;
  }
}
</style>