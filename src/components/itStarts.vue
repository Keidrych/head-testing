<template>
  <!-- root node required -->
  <div>
    <!-- your content -->
    <div class="layout-padding">
      <!-- if you want automatic padding -->
    </div>
  </div>
</template>

<script>
import { Dialog } from 'quasar'

export default {
  data: function () {
    return {
      title: 'My Title',
      myData: 'My description'
    }
  },
  methods: {
    getAsyncData: function () {
      var self = this
      window.setTimeout(function () {
        self.title = 'My async title'
        self.$emit('updateHead')
      }, 3000)
    }
  },
  events: {
    okHead: function () {
      Dialog.create({
        title: 'Alert',
        message: 'Modern HTML5 Single Page Application front-end framework on steroids.'
      }).show()
    }
  },
  route: {
    canReuse: false
  },
  // Usage with context the component
  head: {
    title: {
      inner: 'My title',
      separator: '-',
      complement: 'My Complement'
    },    // Meta tags
    meta: [
      { name: 'application-name', content: 'Name of my application' },
      { name: 'description', content: 'A description of the page', id: 'desc' }, // id to replace intead of create element
      // ...
      // Twitter
      { name: 'twitter:title', content: 'Content Title' },
      // with shorthand
      { n: 'twitter:description', c: 'Content description less than 200 characters' },
      // ...
      // Google+ / Schema.org
      { itemprop: 'name', content: 'Content Title' },
      { itemprop: 'description', content: 'Content Title' },
      // ...
      // Facebook / Open Graph
      { property: 'fb:app_id', content: '123456789' },
      { property: 'og:title', content: 'Content Title' },
      // with shorthand
      { p: 'og:image', c: 'https://example.com/image.jpg' }
      // ...
    ],
    // link tags
    link: [
      { rel: 'canonical', href: 'http://example.com/#!/contact/', id: 'canonical' },
      { rel: 'author', href: 'author', undo: false } // undo property - not to remove the element
      // ...
    ],
    script: [
      { type: 'text/javascript', src: 'cdn/to/script.js', async: true, body: true }, // Insert in body
      // with shorthand
      { t: 'application/ld+json', i: '{ "@context": "http://schema.org" }' }
      // ...
    ],
    style: [
      { type: 'text/css', inner: 'body { background-color: #000; color: #fff}', undo: false }
      // ...
    ]
  }
}
</script>

<style>
</style>
