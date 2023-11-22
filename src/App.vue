<script setup>
import taskCenter from './components/Dashboard/taskCenter.vue';
</script>

<template>
  <header>
    <div class="wrapper">
      <pageTtile msg="TodoList Vue"/>
    </div>
  </header>

  <main>
    <taskCenter />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }
  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
