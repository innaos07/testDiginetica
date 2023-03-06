<template>
  <section class="catalog">
    <h2 class="catalog__category">Название категории</h2>
    <ul class="catalog__list">
      <catalog-item 
        v-for="item in catalogList" 
        :key="item.id" 
        :item="item" 
      />
    </ul>
  </section>
</template>

<script setup>
import CatalogItem from "@/modules/catalog/CatalogItem.vue";

const props = defineProps({
  catalogList: {
    type: Array,
    default: () => [],
  },
});
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";

.catalog {
  flex: 1;

  .catalog__category {
    display: none;
  }

  .catalog__list {
    display: flex;
    flex-wrap: wrap;
    margin: 0 -12px;
    row-gap: 24px;
  }

  @media (max-width: $md-width) {
    .catalog__list {
      overflow-y: scroll;
      height: 100%;
      row-gap: 16px;
    }
    
    .catalog__category {
      display: block;
      padding-left: 8px;
      margin-bottom: 12px;
      font-weight: 400;
      font-size: 22px;
      line-height: 127%;
    }
  }

  @media (max-width: $ssm-width) {
    .catalog__list {
      justify-content: center;
    }
  }
}
</style>
