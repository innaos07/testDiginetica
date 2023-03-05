<template>
  <section class="catalog">
    <ul class="catalog__list">
      <catalog-item v-for="item in catalogList" :key="item.id" :item="item"/>
    </ul>
  </section>
</template>

<script setup>
import CatalogItem from '../components/catalog/CatalogItem.vue';

const props = defineProps({
  catalogList: {
    type: Array,
    default: () => [],
  }
})
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";

.catalog {
  flex: 1;

  .catalog__list {
    display: flex;
    flex-wrap: wrap;
    margin: 0 -12px;
    row-gap: 24px;

    @media (max-width: $md-width) {
      row-gap: 16px;
    }

    @media (max-width: $sm-width) {
      justify-content: center;
    }
  }
}

</style>