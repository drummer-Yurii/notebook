<template>
  <ul>
    <LearningResource
      v-for="res in storedResources"
      :key="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
    ></LearningResource>
  </ul>
</template>

<script>
import LearningResource from './components/learning-resources/LearningResource';
export default {
  name: 'App',
  components: {
    LearningResource,
  },
  data() {
    return {
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
};
</script>

<style>
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
