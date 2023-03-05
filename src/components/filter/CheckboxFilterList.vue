<template>
  <ul class="checkbox-filter__list">
    <li v-for="item in checkboxFilterList" :key="item.id" class="checkbox-filter__item">
      <input
        type="checkbox"
        :value="item.value"
        :id="item.value"
        class="visually-hidden"
      />
      <label :for="item.value"> {{ item.name }}</label>
      <span class="item-filter__quantity">{{ item.quantity }}</span>
    </li>
  </ul>
</template>

<script setup>
const props = defineProps ({
  checkboxFilterList: {
    type: Array,
    default: () => [],
  }
})
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";

.checkbox-filter__list {
  display: flex;
  flex-direction: column;
  row-gap: 12px;

  .checkbox-filter__item {
    position: relative;
    display: flex;
    justify-content: space-between;

    padding-top: 2px;
    padding-bottom: 2px;
    padding-left: 32px;
    padding-right: 16px;

    input ~ label::before {
      position: absolute;
      content: "";
      top: 0;
      left: 0;
      width: 20px;
      height: 20px;
      border: 1px solid $color-border;
      border-radius: 3px;
    }

    input:hover ~ label::before,
    input:focus ~ label::before {
      border: 1px solid $color-brand;
      transition: all 0.5s;
    }

    input:checked ~ label::before {
      background: $color-brand;
      border: 1px solid $color-brand;
      background-image: url("@/assets/image/check-mark.svg");
      background-repeat: no-repeat;
      background-position: center;
      transition: all 0s;
    }
  }
}
</style>