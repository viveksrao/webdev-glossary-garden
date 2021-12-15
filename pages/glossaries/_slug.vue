<script>
export default {
  async asyncData({ $content, route }) {
    const glossary = await $content(`glossaries/${route.params.slug}`).fetch();
    return {
      glossary
    }
  }
}
</script>

<template>
  <main>
    <h1>{{ glossary.title }}</h1>
    <nuxt-content :document="glossary"/>
  </main>
</template>