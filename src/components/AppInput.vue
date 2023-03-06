<template>
  <input
    type="text"
    name="brand"
    :value="modelValue"
    @input="emit('update:modelValue', $event.target.value)"
    class="brand-filter__input"
    :class="{ 'brand-filter__input--fail': isSearchFail }"
    placeholder="Поиск"
  />
</template>

<script setup>
defineProps({
  modelValue: {
    type: String,
    required: "",
  },
  isSearchFail: {
    type: Boolean,
    default: false,
  },
});

const emit = defineEmits(["update:modelValue"]);
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";

.brand-filter__input {
  width: 100%;
  margin-bottom: 16px;
  min-height: 36px;
  padding: 10px 12px;
  padding-left: 36px;
  border: 1px solid $color-border;
  background-color: transparent;
  border-radius: 4px;
  font-family: inherit;
  line-height: 114.3%;
  color: inherit;

  &--fail {
    margin-bottom: 8px;
  }

  &::placeholder {
    font-family: inherit;
    color: $color-font-second;
  }

  &--active {
    padding-right: 36px;
    border-color: $color-light-blue;
  }

  &:hover,
  &:focus {
    border-color: $color-brand;
    outline: none;
    transition: all 0.5s;
  }
}
</style>