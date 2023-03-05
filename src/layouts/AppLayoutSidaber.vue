<template>
  <section class="filter">
    <form action="#" class="filter__form">
      <fieldset class="filter__item item-filter">
        <ul class="filter__category category-filter">
          <li
            v-for="itemCategory in categoryList"
            :key="itemCategory.id"
            class="category-filter__item"
          >
            <div class="category-filter__info">
              <p>{{ itemCategory.name }}</p>
              <span class="category-filter__quantity item-filter__quantity">{{
                itemCategory.quantity
              }}</span>
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
                  <span
                    class="subcategory-filter__quantity item-filter__quantity"
                    >{{ itemSubcategory.quantity }}</span
                  >
                </div>
              </li>
            </ul>
          </li>
        </ul>
      </fieldset>

      <!-- <fieldset class="filter__item item-filter">
        <div class="filter__price price-filter">
          <div class="price-filter__row item-filter__row">
            <h2 class="price-filter__title item-filter__title">Цена</h2>
            <button class="price-filter__btn-clean item-filter__btn-clean">
              Очистить
            </button>
          </div>

          <div class="price-filter__range">
            <div class="price-filter__input price-filter__input--min">
              <input
                type="text"
                name="minPrice"
                placeholder="5 500 ₽"
              />
            </div>
            <span class="price-filter__elem"></span>
            <div class="price-filter__input price-filter__input--max">
              <input
                type="text"
                name="maxPrice"
                placeholder="5 500 ₽"
              />
            </div>
          </div>
        </div>
      </fieldset> -->
      <filter-price></filter-price>

      <fieldset class="filter__item item-filter">
        <div class="filter__brend brend-filter">
          <div class="brend-filter__row item-filter__row">
            <h2 class="brend-filter__title item-filter__title">Бренд</h2>
            <button class="brend-filter__btn-clean item-filter__btn-clean">
              Очистить
            </button>
          </div>
          <div class="brend-filter__search">
            <input
              type="text"
              name="brend"
              :value="searchBrand"
              class="brend-filter__input"
              :class="{ 'brend-filter__input--fail': isSearchFail }"
              placeholder="Поиск"
              @input="setSearchBrand"
            />
            <button
              class="brend-filter__btn-delete"
              :class="{
                'brend-filter__btn-delete--active': isActiveSearchBrand,
              }"
              @click="deleteSearchBrand"
            >
              <svg
                width="13.13"
                height="13.13"
                viewBox="0 0 20 20"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M20.0001 10C20.0001 15.5228 15.5229 20 10.0001 20C4.47721 20 6.10352e-05 15.5228 6.10352e-05 10C6.10352e-05 4.47715 4.47721 0 10.0001 0C15.5229 0 20.0001 4.47715 20.0001 10ZM13.7072 7.70711C14.0977 7.31658 14.0977 6.68342 13.7072 6.29289C13.3166 5.90237 12.6835 5.90237 12.293 6.29289L10.0001 8.58579L7.70717 6.29289C7.31664 5.90237 6.68348 5.90237 6.29295 6.29289C5.90243 6.68342 5.90243 7.31658 6.29295 7.70711L8.58585 10L6.29295 12.2929C5.90243 12.6834 5.90243 13.3166 6.29295 13.7071C6.68348 14.0976 7.31664 14.0976 7.70717 13.7071L10.0001 11.4142L12.293 13.7071C12.6835 14.0976 13.3166 14.0976 13.7072 13.7071C14.0977 13.3166 14.0977 12.6834 13.7072 12.2929L11.4143 10L13.7072 7.70711Z"
                  fill="#333333"
                />
              </svg>
            </button>

            <p v-if="isSearchFail" class="brend-filter__fail-text">
              По вашему запросу ничего не найдено
            </p>
            <checkbox-filter-list :checkboxFilterList="brendList" />
          </div>
        </div>
      </fieldset>

      <fieldset class="filter__item item-filter">
        <div class="filter__size size-filter">
          <div class="size-filter__row item-filter__row">
            <h2 class="size-filter__title item-filter__title">Размер</h2>
            <button class="size-filter__btn-clean item-filter__btn-clean">
              Очистить
            </button>
          </div>
          <checkbox-filter-list :checkboxFilterList="sizeList" />
        </div>
      </fieldset>
    </form>
  </section>
</template>

<script setup>
import { ref } from "vue";
import CheckboxFilterList from "@/components/filter/CheckboxFilterList.vue";
import FilterPrice from "@/components/filter/FilterPrice.vue";
const isSearchFail = ref(false);
const minPrice = ref('');


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
const brendList = [
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
];
const isActiveSearchBrand = ref(false);
const searchBrand = ref("");

const setSearchBrand = (e) => {
  e.target.value
    ? (isActiveSearchBrand.value = true)
    : (isActiveSearchBrand.value = false);
  searchBrand.value = e.target.value.trim();
};

const deleteSearchBrand = () => {
  searchBrand.value = "";
  isActiveSearchBrand.value = false;
};
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";

.filter {
  display: flex;
  flex-direction: column;
  width: 280px;
  height: 100vh;
  margin-right: 36px;
  border: 1px solid red;

  .filter__form {
    display: flex;
    flex-direction: column;
  }

  .filter__item {
    &:not(:last-child) {
      margin-bottom: 28px;
    }
  }

  .item-filter__quantity {
    font-size: 12px;
    line-height: 117%;
    color: $color-font-second;
  }

  .item-filter__row {
    display: flex;
    justify-content: center;
    margin-bottom: 16px;

    &--active {
      justify-content: space-between;
      align-items: flex-end;
    }

    .item-filter__title {
      font-weight: 700;
      font-size: 16px;
      line-height: 125%;
      text-align: center;
    }

    .item-filter__btn-clean {
      display: none;
      &--active {
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

  // .price-filter {
  //   .price-filter__range {
  //     position: relative;
  //     display: flex;
  //     justify-content: space-between;
  //     align-items: center;
  //   }

  //   .price-filter__elem {
  //     width: 10px;
  //     height: 1px;
  //     background: $color-border;
  //   }

  //   .price-filter__input {
  //     &--min::before,
  //     &--max::before {
  //       position: absolute;
  //       display: flex;
  //       align-items: center;
  //       justify-content: center;
        
  //       width: 12px;
  //       height: 14px;
  //       font-size: 12px;
  //       line-height: 117%;
  //       color: $color-font-second;
  //     }

  //     &--min::before {
  //       content: 'от';
  //       top: 11px;
  //       left: 8px;
  //     }

  //     &--max::before {
  //       content: 'до';
  //       top: 11px;
  //       left: 8px;
  //     }

  //     input {
  //       width: 119px;
  //       padding: 10px 8px;
  //       padding-left: 26px;
  //       border: 1px solid $color-border;
  //       border-radius: 4px;

  //       &:hover,
  //       &:focus {
  //         outline: none;
  //         border-color: $color-brand;
  //         transition: all 0.5s;
  //       }
  //     }
  //   }

  //   // .price-filter__input--max {
  //   //     &::after {
  //   //       position: absolute;
  //   //       display: block;
  //   //       content: 'j';
  //   //       top: 11px;
  //   //       left: 8px;
  //   //       width: 12px;
  //   //       height: 16px;
  //   //       background: red;
  //   //     }
  //   //   }
  // }

  .brend-filter {
    .brend-filter__search {
      position: relative;

      &::before {
        content: "";
        position: absolute;
        top: 10px;
        left: 12px;
        width: 16px;
        height: 16px;
        background-image: url("@/assets/image/search-2.svg");
        background-repeat: no-repeat;
        background-position: center;
      }

      .brend-filter__input {
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

      .brend-filter__btn-delete {
        display: none;
        position: absolute;
        content: "";
        cursor: pointer;
        top: 10px;
        right: 12px;
        width: 16px;
        height: 16px;
        background-color: transparent;

        svg {
          width: 13.13px;
          height: 13.13px;

          path {
            fill: #c2c2c2;
          }
        }

        &:hover,
        &:focus {
          svg path {
            fill: $color-font-main;
            transition: all 0.5s;
          }
        }

        &--active {
          display: flex;
          justify-content: center;
          align-items: center;
        }
      }

      .brend-filter__fail-text {
        margin-bottom: 16px;
      }

      // .brend-filter__list {
      //   display: flex;
      //   flex-direction: column;
      //   row-gap: 12px;

      //    .brend-filter__item {
      //     position: relative;
      //     display: flex;
      //     justify-content: space-between;

      //     padding-top: 2px;
      //     padding-bottom: 2px;
      //     padding-left: 32px;
      //     padding-right: 16px;

      //       input~label::before {
      //         position: absolute;
      //         content: '';
      //         top: 0;
      //         left: 0;
      //         width: 20px;
      //         height: 20px;
      //         border: 1px solid $color-border;
      //         border-radius: 3px;
      //     }

      //     input:hover ~ label::before,
      //     input:focus ~ label::before {
      //       border: 1px solid $color-brand;
      //       transition: all 0.5s;
      //     }

      //     input:checked~label::before {
      //       background: $color-brand;
      //       border: 1px solid $color-brand;
      //       background-image: url('@/assets/image/check-mark.svg');
      //       background-repeat: no-repeat;
      //       background-position: center;
      //       transition: all 0s;
      //     }
      //   }
      // }
    }
  }

  @media (max-width: $md-width) {
    display: none;
  }
}
</style>