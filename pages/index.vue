<template>
  <h1>Build a Digital Garden with Nuxt and Nuxt Content Module</h1>
</template>

<script>
export default {
  name: 'IndexPage',
  mounted() {
    console.log(this.$content);
  }
}
</script>