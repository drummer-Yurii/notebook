<template>
  <BaseCard>
    <BaseButton @click="setSelectedTab('stored-resource')" :mode="storedResButtonMode">Stored Notes</BaseButton>
    <BaseButton @click="setSelectedTab('add-resource')" :mode="addResButtonMode">Add Note</BaseButton>
  </BaseCard>
  <component :is="selectedTab"></component>
</template>

<script>
import BaseButton from '../UI/BaseButton';
import BaseCard from '../UI/BaseCard';
import StoredResource from './StoredResource.vue';
import AddResource from './AddResource.vue';
export default {
  components: {
    BaseButton,
    BaseCard,
    StoredResource,
    AddResource
  },
  name: 'TheResource',
  data() {
    return {
      selectedTab: 'stored-resource',
      storedResources: [
        {
          id: 'official-gide',
          title: 'Official Gide',
          description: 'The official vue.js Documentation',
          link: 'https://vue.js.com',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to Google',
          link: 'https://google.com',
        },
      ],
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
  },

  computed: {
    storedResButtonMode() {
        return this.selectedTab === 'stored-resource' ? null : 'flat'
    },
    addResButtonMode() {
        return this.selectedTab === 'add-resource' ? null : 'flat'
    }
  },

  provide() {
    return {
        resource: this.storedResources
    }
  }
};
</script>

<style scoped></style>
