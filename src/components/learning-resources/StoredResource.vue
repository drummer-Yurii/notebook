<template>
  <ul>
    <learning-resource
      v-for="res in resource"
      :key="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
    ></learning-resource>
  </ul>
</template>

<script>
import LearningResource from './LearningResource.vue';
export default {
  name: 'StoredResource',
  components: {
    LearningResource,
  },
  props: ['resource']
};
</script>

LearningResource
<style scoped>
ul {
    list-style: none;
    margin: 0;
    padding: 0;
    margin: auto;
    max-width: 40rem;
}
</style>
