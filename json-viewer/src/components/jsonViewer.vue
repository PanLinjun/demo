<template>
  <div>
      <pre id="result" class="viewer">
      </pre>
  </div>
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
      json: '',
      html: ''
    }
  },
  mounted() {
    this.json = JSON.stringify(this.data, null, 2)
    this.html = this.syntaxHighlight(this.json)
    console.log(typeof this.html)
    const pre = document.getElementById('result')
    pre.innerHTML = this.html
    console.log(pre)
  },
  methods: {
    syntaxHighlight(json) {
      json = json.replace(/&/g, '&').replace(/</g, '<').replace(/>/g, '>')
      console.log(json)
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
  .viewer {
    text-align: left;
    margin-left: 300px;
    font-size: 20px;
    outline: 1px solid #ccc;
  }

  .number {
    color: dodgerblue;
  }
  .boolean {
    color: red;
  }
  .null {
    color: magenta;
  }
  .key {
    color: green;
  }
</style>