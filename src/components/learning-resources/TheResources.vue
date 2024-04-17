<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')" :mode="storedButtonMode"
      >Stored Resources</base-button
    >
    <base-button @click="setSelectedTab('add-resource')" :mode="addButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue'
import AddResource from './AddResource.vue'

export default {
  components: {
    StoredResources,
    AddResource
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation',
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
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      deleteResource: this.deleteResource
    }
  },
  computed: {
    storedButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat'
    },
    addButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat'
    }
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab
    },
    addResource(title, description, link) {
      const newResource = {
        id: new Date().toISOString(),
        title,
        description,
        link
      }
      this.storedResources.unshift(newResource)
      this.selectedTab = 'stored-resources'
    },
    deleteResource(resId) {
      /* This removes the element but creates a new storedResources array which isn't what Vue displays
      this.storedResources = this.storedResources.filter(res => res.id !== resId) */

      // Vue passes the original array so you have to alter THAT storedResources array
      const resIndex = this.storedResources.findIndex((res) => res.id === resId)
      this.storedResources.splice(resIndex, 1)
    }
  }
}
</script>
