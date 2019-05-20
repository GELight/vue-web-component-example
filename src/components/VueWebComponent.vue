<template>
  <div v-html="dynamicHtml"></div>
</template>

<script>
export default {
  data () {
    return {
      loadedHtml: null
    }
  },
  props: {
    msg: {
      type: String,
      required: false
    }
  },
  computed: {
    dynamicHtml () {
      if (typeof this.loadedHtml === 'string') {
        return this.loadedHtml
      }
      return ''
    }
  },
  mounted () {
    this.loadedHtml = this.load('/example-html-page-snippet.html')
  },
  methods: {
    load (url) {
      return fetch(url, {
        mode: 'no-cors',
        method: 'get'
      }).then(response => {
        return response.text()
      }).then(html => {
        return html
      })
    }
  }
}
</script>
