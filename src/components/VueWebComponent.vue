<script>
export default {
  data () {
    return {
      template: null
    }
  },
  props: {
    msg: {
      type: String,
      required: false
    }
  },
  render (h) {
    // if (!this.template) {
    //   return h('div', '')
    // } else {
    //   return h(this.load('www.google.de'))
    // }
    return h(this.load('http://www.google.de'))
  },
  methods: {
    load (url) {
      return fetch(url, {
        mode: 'no-cors',
        method: 'get'
      }).then(response => {
        return response.text()
      })
    }
  }
}
</script>
