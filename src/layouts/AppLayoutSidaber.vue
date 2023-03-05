<template>
  <section class="filter">
    <form action="#" class="filter__form">
      <ul class="">
    
      </ul>
    </form>
  </section>
</template>

<script setup>
  // const categoryList
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

  @media (max-width: $md-width) {
    display: none;
  }
}
</style>