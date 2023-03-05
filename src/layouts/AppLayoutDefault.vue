<template>
  <div class="app__layout">
    <app-layout-header />
    <main>
      <div class="container">
        <div class="content">
           <app-layout-sidaber />
           <slot/>
        </div>
      </div>
    </main>
   
  </div>
</template>

<script setup>
import AppLayoutHeader from "./AppLayoutHeader.vue";
import AppLayoutSidaber from "./AppLayoutSidaber.vue";
</script>

<style>
.content {
  display: flex;
  

}
</style>