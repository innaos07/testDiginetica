<template>
  <div
    class="filter__header"
    :class="{ 'filter__header--active': isActiveInput }"
  >
    <h2 class="filter__title"><slot /></h2>
    <button
      class="filter__btn-clean"
      :class="{ 'filter__btn-clean--active': isActiveInput }"
    >
      Очистить
    </button>
  </div>
</template>

<script setup>
const props = defineProps({
  isActiveInput: {
    type: Boolean,
    default: false,
  },
});
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";

.filter__header {
  display: flex;
  justify-content: center;
  margin-bottom: 16px;

  &--active {
    justify-content: space-between;
    align-items: flex-end;
  }

  .filter__title {
    font-weight: 700;
    font-size: 16px;
    line-height: 125%;
    text-align: center;
  }

  .filter__btn-clean {
    display: none;
    &--active {
      display: block;
      font-size: 12px;
      line-height: 1;
      color: $color-font-second;
      text-decoration: underline;
      background: transparent;
      cursor: pointer;

      &:hover,
      &:focus {
        color: $color-font-main;
        transition: all 0.5s;
      }
    }
  }
}
</style>