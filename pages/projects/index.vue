<template lang="pug">

</template>

<script>
export default {
  head() {
    return {
      title: 'Alain Cao Van Truong | Projects',
      meta: [
        { hid: 'description', name: 'description', content: 'Discover my main projects since I have started web and mobile development.' }
      ]
    }
  },
  computed: {
    projects() {
      return this.$store.state.projects
    }
  }
}
</script>