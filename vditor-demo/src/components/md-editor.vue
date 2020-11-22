<template>
  <div style="display: flex">
    <div id="preview"></div>
    <div id="outline" style="position: fixed; margin-left: 900px"></div>
  </div>
</template>

<script>
import Vditor from 'vditor/dist/method.min'

export default {
  name: "mdEditor",
  props: ['markdown'],
  mounted() {
    console.log(this.markdown)
  },
  watch: {
    markdown() {
      Vditor.preview(document.getElementById('preview'), this.markdown, {
        speech: {
          enable: true,
        },
        anchor: 1,
        after() {
          const outline = document.getElementById('outline')
          Vditor.outlineRender(document.getElementById('preview'), outline)
        }
      })
    }
  }
}
</script>

<style scoped>

</style>