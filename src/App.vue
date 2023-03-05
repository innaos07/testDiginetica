<template>
  <app-layout>
    <catalog-view :catalogList="store.products"/>
  </app-layout>
</template>

<script setup>
import { reactive } from "vue";
import products from "@/data/products.json"
import AppLayout from "@/layouts/AppLayoutDefault.vue";
import CatalogView from "@/views/CatalogView.vue"

const store = reactive ({
  products: products,
})
</script>

<style lang="scss">
@import "@/assets/scss/main.scss";

</style>
