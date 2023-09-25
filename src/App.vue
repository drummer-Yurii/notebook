<template>
  <TheHeader title="Notebook"></TheHeader>
  <StoredResource :resource="storedResources"></StoredResource>
</template>

<script>
import TheHeader from './components/layouts/TheHeader'
import StoredResource from './components/learning-resources/StoredResource'
export default {
  name: 'App',
  components: {
    TheHeader,
    StoredResource,
    
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
