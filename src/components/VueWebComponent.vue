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
    return h(this.load('www.google.de'))
  },
  methods: {
    load (url) {
      return fetch(url)
        .then(response => {
          return response.text()
        })
        .then(html => {
          // Initialize the DOM parser
          var parser = new DOMParser()

          // Parse the text
          var doc = parser.parseFromString(html, 'text/html')
          // You can now even select part of that html as you would in the regular DOM
          // Example:
          // var docArticle = doc.querySelector('article').innerHTML
          console.log(doc)
          return doc
        })
        .catch(err => {
          console.log('Failed to fetch page: ', err)
        })
    }
  }
}
</script>
