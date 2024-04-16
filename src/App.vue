<template>
  <ul>
    <learning-resource
      v-for="resource in storedResources"
      :key="resource.id"
      :title="resource.title"
      :description="resource.description"
      :link="resource.link"
    ></learning-resource>
  </ul>
</template>

<script>
import LearningResource from './components/learning-resources/LearningResource.vue'

export default {
  components: {
    LearningResource
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
