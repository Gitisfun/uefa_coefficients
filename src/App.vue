<template>
  <div id="app">
    <div>
      <Header />
    </div>
    <router-view/>
  </div>
</template>

<script>
import Header from '@/layouts/Header.vue'

export default {
  name: "App",
  components: {
    Header
  }
}
</script>

<style>
body {
background-color: green;

}
</style>