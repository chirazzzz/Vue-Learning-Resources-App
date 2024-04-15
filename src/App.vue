<template>
  <ul v-for="resource in storedResources" :key="resource">
    <li>{{ resource }}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      storedResources: [
        { id: 'offical-guide', title: 'Offical Guide', description: 'The offical Vue.js documentation', link: 'https://vuejs.org' },
        { id: 'stack-overflow', title: 'Stack Overflow', description: 'The best Q&A site for computer programmers', link: 'https://stackoverflow.com/' },
        { id: 'js-docs', title: 'MDN - JavaScript guide', description: 'Complete guide to JavaScript', link: 'https://developer.mozilla.org' },
      ]
    }
  },
}
</script>