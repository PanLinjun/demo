<template>
  <div id="app">
    <json-viewer :data="data"></json-viewer>
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
      data: {
        id: 1,
        name: 'pan',
        property: {
          color: 'red',
          address: 'earth',
          single: false,
          brother: null
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
