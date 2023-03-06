<template>
  <div class="app__layout">
    <app-layout-header />
    <main>
      <div class="container">
        <div class="content">
           <app-layout-sidebar />
           <slot/>
        </div>
      </div>
    </main>
   
  </div>
</template>

<script setup>
import AppLayoutHeader from "./AppLayoutHeader.vue";
import AppLayoutSidebar from "./AppLayoutSidebar.vue";
</script>

<style>
.content {
  display: flex;
}
</style>