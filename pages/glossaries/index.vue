<script>
  export default {
    async asyncData({ $content }){
      const glossaries = await $content('glossaries').sortBy("publishOn","desc").fetch();
      return{
        glossaries
      }
    },
    name: 'GlossariesPage',
    data: () => ({
      selectedTag: ""
    }),
    computed: {
      displayedGlossaries(){
        if(this.selectedTag){
          return this.glossaries.filter(glossary => glossary.tags.includes(this.selectedTag));
        }else{
          return this.glossaries;
        }
      } 
    }
  }
</script>
<template>
  <main>
    <h1>WebDev Glossary</h1>
    <p class="lead" v-show="selectedTag">Filtered by: {{ selectedTag }} <button class="btn btn-primary" @click="selectedTag = ''">Clear</button></p>
    <ul>
      <li v-for="glossary in displayedGlossaries" :key="glossary.slug + glossary.createdAt" class="lead mb-2">
        <h2><nuxt-link :to="`/glossaries/${glossary.slug}`" class="text-decoration-none">{{ glossary.title }}</nuxt-link></h2>
        <p class="lead">Publish on: {{ new Date(glossary.publishOn)}}</p>
        <ul class="list-inline">
          <li class="list-inline-item" v-for="tag in glossary.tags" :key="glossary.slug + tag" @click="selectedTag = tag">
            <span class="badge bg-primary">{{ tag }}</span>
          </li>
        </ul>
      </li>
    </ul>
  </main>
</template>