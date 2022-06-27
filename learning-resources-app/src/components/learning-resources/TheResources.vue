<template>
  <base-card>
    <base-button
      @click="setSelected('stored-resources')"
      :mode="storedResBtnMode"
      >Stored Resources</base-button
    >
    <base-button @click="setSelected('add-resource')" :mode="addResBtnMode"
      >Add Resource</base-button
    >
  </base-card>
  <component :is="selectedTab" @submit-data="submitResource"></component>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';
export default {
  components: { StoredResources, AddResource },

  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: Math.floor(Math.random() * 100) + 2,
          title: 'Vue.Js',
          description: 'Vue is a great framework.',
          link: 'https://vuejs.org',
        },
        {
          id: Math.floor(Math.random() * 100) + 2,
          title: 'Vue.Js',
          description: 'Vue is a great framework.',
          link: 'https://vuejs.org',
        },
      ],
    };
  },

  provide() {
    return {
      resources: this.storedResources,
      deleteResource: this.removeResource,
    };
  },
  methods: {
    setSelected(tab) {
      this.selectedTab = tab;
    },
    submitResource(title, description, link) {
      const newResource = {
        id: Math.floor(Math.random() * 100) + 2,
        title: title,
        description: description,
        link: link,
      };
      this.storedResources.push(newResource);
      this.selectedTab = 'stored-resources';
    },
    removeResource(resId) {
      const index = this.storedResources.findIndex((res) => res.id === resId);
      this.storedResources.splice(index, 1);
    },
  },

  computed: {
    storedResBtnMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResBtnMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },
};
</script>

<style scoped>
div {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 32px;
}
</style>
