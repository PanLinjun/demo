<template>
  <pre id="viewer"></pre>
</template>

<script>
export default {
  name: "jsonViewer",
  props: {
    data: {
      type: Object,
      default: () => ({})
    }
  },
  data() {
    return {
      json: ''
    }
  },
  mounted() {
    this.json = JSON.stringify(this.data, null, 2)
    const pre = document.getElementById('viewer')
    pre.innerHTML = this.syntaxHighlight(this.json)
  },
  methods: {
    syntaxHighlight(json) {
      if (typeof json != 'string') {
        json = JSON.stringify(json, undefined, 2);
      }
      json = json.replace(/&/g, '&').replace(/</g, '<').replace(/>/g, '>');
      return json.replace(/("(\\u[a-zA-Z0-9]{4}|\\[^u]|[^\\"])*"(\s*:)?|\b(true|false|null)\b|-?\d+(?:\.\d*)?(?:[eE][+\-]?\d+)?)/g, function(match) {
        var cls = 'number';
        if (/^"/.test(match)) {
          if (/:$/.test(match)) {
            cls = 'key';
          } else {
            cls = 'string';
          }
        } else if (/true|false/.test(match)) {
          cls = 'boolean';
        } else if (/null/.test(match)) {
          cls = 'null';
        }
        return '<span class="' + cls + '">' + match + '</span>';
      });
    }
  }
}
</script>

<style>
  pre {
    text-align: left;
    outline: 1px solid #ccc;
    padding: 5px;
    margin: 5px;
  }
  .number { color: deepskyblue; }
  .boolean { color: red; }
  .null { color: magenta; }
  .key { color: green; }
</style>