<template>
  <fieldset class="filter__item item-filter">
    <ul class="filter__category category-filter item-filter__scroll">
      <li
        v-for="itemCategory in categoryList"
        :key="itemCategory.id"
        class="category-filter__item"
      >
        <div class="category-filter__info">
          <p>{{ itemCategory.name }}</p>
          <span class="category-filter__quantity item-filter__quantity">{{ itemCategory.quantity }}</span>
        </div>

        <ul
          v-if="itemCategory.subcategoryList.length"
          class="filter__subcategory subcategory-filter"
        >
          <li
            v-for="itemSubcategory in itemCategory.subcategoryList"
            :key="itemSubcategory.id"
            class="subcategory-filter__item"
          >
            <div class="subcategory-filter__info">
              <p>{{ itemSubcategory.name }}</p>
              <span class="subcategory-filter__quantity item-filter__quantity">{{ itemSubcategory.quantity }}</span>
            </div>
          </li>
        </ul>
      </li>
    </ul>
  </fieldset>
</template>

<script setup>
const props = defineProps({
  categoryList: {
    type: Array,
    default: () => [],
  },
});
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";

.category-filter {
  .category-filter__info,
  .subcategory-filter__info {
    display: flex;
    justify-content: space-between;

    &:hover,
    &:focus {
      border-radius: 5px;
      background: $color-font-bg;
      transition: all 0.5s;
    }
  }

  .category-filter__info {
    padding: 7px 8px;
  }

  .subcategory-filter__info {
    padding: 7px 8px;
    padding-left: 32px;
  }
}
</style>