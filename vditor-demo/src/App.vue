<template>
  <div id="app">
    <md-editor :markdown="markdown"></md-editor>
  </div>
</template>

<script>
const toMarkdown = require('to-markdown')
import mdEditor from './components/md-editor'

export default {
  name: 'App',
  components: {
    mdEditor
  },
  data() {
    return {
      html: '',
      markdown: ''
    }
  },
  mounted() {
    this.html = require('./test.md')
    this.markdown = toMarkdown(this.html)
  }
}
</script>

<style>
</style>
