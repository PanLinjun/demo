<template>
  <div id="app">
    <json-viewer :data="test"></json-viewer>
  </div>
</template>

<script>
import jsonViewer from "./components/jsonViewer"

export default {
  name: 'App',
  components: {
    jsonViewer
  },
  data() {
    return {
      test: {
        id: 1,
        value: 'ming',
        property: {
          address: 'earth',
          single: true,
          car: null
        }
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
