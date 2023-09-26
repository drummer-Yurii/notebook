<template>
  <BaseCard>
    <BaseButton @click="setSelectedTab('stored-resource')" :mode="storedResButtonMode"
      >Stored Notes</BaseButton
    >
    <BaseButton @click="setSelectedTab('add-resource')" :mode="addResButtonMode"
      >Add Note</BaseButton
    >
  </BaseCard>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
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
    AddResource,
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
    addNote(title, description, link) {
      const newNote = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: link,
      };
      this.storedResources.unshift(newNote);
      this.selectedTab = 'stored-resource';
    },
    removeNote(resId) {
      const resIndex = this.storedResources.findIndex((res) => (res.id = resId));
      this.storedResources.splice(resIndex, 1);
    },
  },

  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resource' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },

  provide() {
    return {
      resource: this.storedResources,
      addNote: this.addNote,
      removeNote: this.removeNote
    };
  },
};
</script>

<style scoped></style>
