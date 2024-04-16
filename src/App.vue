<template>
  <the-header title="Learning Resources"></the-header>
  <stored-resources :resources="storedResources"></stored-resources>
</template>

<script>
import TheHeader from './components/layout/TheHeader.vue'
import StoredResources from './components/learning-resources/StoredResources.vue'

export default {
  components: {
    TheHeader,
    StoredResources
  },
  data() {
    return {
      storedResources: [
        {
          id: 'offical-guide',
          title: 'Offical Guide',
          description: 'The offical Vue.js documentation',
          link: 'https://vuejs.org'
        },
        {
          id: 'stack-overflow',
          title: 'Stack Overflow',
          description: 'The best Q&A site for computer programmers',
          link: 'https://stackoverflow.com/'
        },
        {
          id: 'js-docs',
          title: 'MDN - JavaScript guide',
          description: 'Complete guide to JavaScript',
          link: 'https://developer.mozilla.org'
        }
      ]
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
