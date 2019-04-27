<template>
  <div id="app">
    <div id="wrap">
      <MainLayout/>
    </div>
  </div>
</template>

<script>
import MainLayout from './components/MainLayout.vue'

export default {
  name: 'app',
  components: {
    MainLayout
  },
}
</script>

<style>
#wrap {
  display: flex;
  justify-content: center;
  margin-top: 4em
}
</style>
