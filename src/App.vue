<template>
  <TheHeader title="Notebook"></TheHeader>
  <TheResource></TheResource>
</template>

<script>
import TheResource from './components/learning-resources/TheResource'
import TheHeader from './components/layouts/TheHeader'
export default {
  name: 'App',
  components: {
    TheResource,
    TheHeader,
  },
  data() {
    return {
      
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
