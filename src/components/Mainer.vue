<template>
<main>
  <div v-if="film.length != 0">
    <div class="col px-1 py-2" v-for="element in film" :key="`film ID-${element.id}`">
      <Post :poster="element.poster_path" :title="element.title" :originalTitle="element.original_language" :language="element.original_language" :vote="element.vote_average"/>
    </div>

    <div class="col px-1 py-2" v-for="element in serie" :key="`serie ID-${element.id}`">
      <Post :poster="element.poster_path" :title="element.name" :originalTitle="element.original_name" :language="element.original_language" :vote="element.vote_average" />
    </div>
  </div>

  <div v-else class="empty">
    <h2>Scegli cosa guardare comodamente sul tuo divano!!</h2>
  </div>
</main>
  
</template>

<script>
import Post from '@/components/Post.vue'

export default {
    name: 'Mainer',
    components: {
      Post,
    },
    props: {
      film: Array,
      serie: Array, 
    }
}
</script>

<style scoped lang="scss">
  main{
    background-color: dodgerblue;
  }
</style>