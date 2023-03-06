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
import { ref } from "vue";
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

  // .item-filter__header {
  //   display: flex;
  //   justify-content: center;
  //   margin-bottom: 16px;

  //   &--active {
  //     justify-content: space-between;
  //     align-items: flex-end;
  //   }

  //   .item-filter__title {
  //     font-weight: 700;
  //     font-size: 16px;
  //     line-height: 125%;
  //     text-align: center;
  //   }

  //   .item-filter__btn-clean {
  //     display: none;
  //     &--active {
  //       font-size: 12px;
  //       line-height: 1;
  //       color: $color-font-second;
  //       text-decoration: underline;
  //       background: transparent;
  //       cursor: pointer;

  //       &:hover,
  //       &:focus {
  //         color: $color-font-main;
  //         transition: all 0.5s;
  //       }
  //     }
  //   }
  // }

  // .brend-filter {
  //   .brend-filter__search {
  //     position: relative;

  //     &::before {
  //       content: "";
  //       position: absolute;
  //       top: 10px;
  //       left: 12px;
  //       width: 16px;
  //       height: 16px;
  //       background-image: url("@/assets/image/search-2.svg");
  //       background-repeat: no-repeat;
  //       background-position: center;
  //     }

  //     .brend-filter__input {
  //       width: 100%;
  //       margin-bottom: 16px;
  //       min-height: 36px;
  //       padding: 10px 12px;
  //       padding-left: 36px;
  //       border: 1px solid $color-border;
  //       background-color: transparent;
  //       border-radius: 4px;
  //       font-family: inherit;
  //       line-height: 114.3%;
  //       color: inherit;

  //       &--fail {
  //         margin-bottom: 8px;
  //       }

  //       &::placeholder {
  //         font-family: inherit;
  //         color: $color-font-second;
  //       }

  //       &--active {
  //         padding-right: 36px;
  //         border-color: $color-light-blue;
  //       }

  //       &:hover,
  //       &:focus {
  //         border-color: $color-brand;
  //         outline: none;
  //         transition: all 0.5s;
  //       }
  //     }

  //     .brend-filter__btn-delete {
  //       display: none;
  //       position: absolute;
  //       content: "";
  //       cursor: pointer;
  //       top: 10px;
  //       right: 12px;
  //       width: 16px;
  //       height: 16px;
  //       background-color: transparent;

  //       svg {
  //         width: 13.13px;
  //         height: 13.13px;

  //         path {
  //           fill: #c2c2c2;
  //         }
  //       }

  //       &:hover,
  //       &:focus {
  //         svg path {
  //           fill: $color-font-main;
  //           transition: all 0.5s;
  //         }
  //       }

  //       &--active {
  //         display: flex;
  //         justify-content: center;
  //         align-items: center;
  //       }
  //     }

  //     .brend-filter__fail-text {
  //       margin-bottom: 16px;
  //     }

  //     // .brend-filter__list {
  //     //   display: flex;
  //     //   flex-direction: column;
  //     //   row-gap: 12px;

  //     //    .brend-filter__item {
  //     //     position: relative;
  //     //     display: flex;
  //     //     justify-content: space-between;

  //     //     padding-top: 2px;
  //     //     padding-bottom: 2px;
  //     //     padding-left: 32px;
  //     //     padding-right: 16px;

  //     //       input~label::before {
  //     //         position: absolute;
  //     //         content: '';
  //     //         top: 0;
  //     //         left: 0;
  //     //         width: 20px;
  //     //         height: 20px;
  //     //         border: 1px solid $color-border;
  //     //         border-radius: 3px;
  //     //     }

  //     //     input:hover ~ label::before,
  //     //     input:focus ~ label::before {
  //     //       border: 1px solid $color-brand;
  //     //       transition: all 0.5s;
  //     //     }

  //     //     input:checked~label::before {
  //     //       background: $color-brand;
  //     //       border: 1px solid $color-brand;
  //     //       background-image: url('@/assets/image/check-mark.svg');
  //     //       background-repeat: no-repeat;
  //     //       background-position: center;
  //     //       transition: all 0s;
  //     //     }
  //     //   }
  //     // }
  //   }
  // }

  @media (max-width: $md-width) {
    display: none;
  }
}
</style>