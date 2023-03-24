<script setup>
import TodoHeader from './components/TodoHeader.vue';

</script>

<template>
  <div>
    <TodoHeader />
    <RouterView />
  </div>
</template>

<style lang="scss">

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  margin: 0;
}
</style>
