<template>
  <section class="filter">
    <form action="#" class="filter__form">
      <category-filter :categoryList="categoryList"></category-filter>
      <filter-price></filter-price>
      <brand-filter :brandList="brandList"></brand-filter>
      <size-filter :sizeList="sizeList"></size-filter>
    </form>
  </section>
</template>

<script setup>
import CategoryFilter from "@/modules/filter/CategoryFilter.vue";
import BrandFilter from "@/modules/filter/BrandFilter.vue"
import FilterPrice from "@/modules/filter/FilterPrice.vue";
import SizeFilter from "@/modules/filter/SizeFilter.vue";

const categoryList = [
  {
    id: 1,
    name: "Название категории",
    quantity: 3,
    subcategoryList: [
      {
        id: 2,
        name: "Название подкатегории",
        quantity: 3,
      },
      {
        id: 2,
        name: "Название подкатегории",
        quantity: 3,
      },
      {
        id: 1,
        name: "Название подкатегории",
        quantity: 3,
      },
    ],
  },
];
const brandList = [
  {
    id: 1,
    name: "Атрибут",
    quantity: 3,
    value: "brend1",
  },
  {
    id: 2,
    name: "Атрибут",
    quantity: 3,
    value: "brend2",
  },
  {
    id: 3,
    name: "Атрибут",
    quantity: 3,
    value: "brend3",
  },
  {
    id: 4,
    name: "Атрибут",
    quantity: 3,
    value: "brend4",
  },
  {
    id: 5,
    name: "Атрибут",
    quantity: 3,
    value: "brend5",
  },
  {
    id: 6,
    name: "Атрибут",
    quantity: 3,
    value: "brend6",
  },
  {
    id: 7,
    name: "Атрибут",
    quantity: 3,
    value: "brend5",
  },
  {
    id: 8,
    name: "Атрибут",
    quantity: 3,
    value: "brend6",
  },
];
const sizeList = [
  {
    id: 1,
    name: "Атрибут",
    quantity: 3,
    value: "size1",
  },
  {
    id: 2,
    name: "Атрибут",
    quantity: 3,
    value: "size2",
  },
  {
    id: 3,
    name: "Атрибут",
    quantity: 3,
    value: "size3",
  },
  {
    id: 4,
    name: "Атрибут",
    quantity: 3,
    value: "size4",
  },
  {
    id: 5,
    name: "Атрибут",
    quantity: 3,
    value: "size5",
  },
  {
    id: 6,
    name: "Атрибут",
    quantity: 3,
    value: "size6",
  },
  {
    id: 7,
    name: "Атрибут",
    quantity: 3,
    value: "size5",
  },
  {
    id: 8,
    name: "Атрибут",
    quantity: 3,
    value: "size6",
  },
];
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";

.filter {
  display: flex;
  flex-direction: column;
  width: 280px;
  height: 100%;
  margin-right: 36px;

  .filter__form {
    display: flex;
    flex-direction: column;
  }

  .filter__item {
    &:not(:last-child) {
      margin-bottom: 28px;
    }
  }
  
  .item-filter {
    .item-filter__scroll {
      max-height: 180px;
      overflow-y: scroll;
      scrollbar-width: 3px;
      scrollbar-color: #CBCBCB; 

      &::-webkit-scrollbar {
        width: 3px;
      }

      &::-webkit-scrollbar-thumb {
        background: #CBCBCB;
        border-radius: 10px;
      }
    }
  }

  .item-filter__quantity {
    font-size: 12px;
    line-height: 117%;
    color: $color-font-second;
  }

  @media (max-width: $md-width) {
    display: none;
  }
}
</style>