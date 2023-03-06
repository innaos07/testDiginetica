<template>
  <fieldset class="filter__item item-filter">
    <div class="filter__brand brand-filter">
      <header-filter :isActiveInput="isActiveSearchBrand">Очистить</header-filter>
      
      <div class="brand-filter__search">
        <app-input v-model="searchBrand" :isSearchFail="isSearchFail" />
        <button
          class="brand-filter__btn-delete"
          :class="{ 'brand-filter__btn-delete--active': isActiveSearchBrand }"
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
      </div>

      <p v-if="isSearchFail" class="brand-filter__fail-text"> По вашему запросу ничего не найдено </p>
      <checkbox-filter-list 
        :checkboxFilterList="brandList" 
        v-model="checkList"
      />
    </div>
  </fieldset>
</template>

<script setup>
import { ref, watch } from "vue";
import HeaderFilter from "./HeaderFilter.vue";
import CheckboxFilterList from "@/modules/filter/CheckboxFilterList.vue";
import AppInput from "../../components/AppInput.vue";

const props = defineProps({
  brandList: {
    type: Array,
    default: () => [],
  },
});

const isActiveSearchBrand = ref(false);
const isSearchFail = ref(false);
const searchBrand = ref("");
const checkList = ref([]);

watch(searchBrand, () => {
  searchBrand.value
    ? (isActiveSearchBrand.value = true)
    : (isActiveSearchBrand.value = false);
});

const deleteSearchBrand = () => {
  searchBrand.value = "";
  isActiveSearchBrand.value = false;
};
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";

.brand-filter {
  .brand-filter__search {
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

    .brand-filter__btn-delete {
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

    .brand-filter__fail-text {
      margin-bottom: 16px;
    }
  }
}
</style>
