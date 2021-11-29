<template>
  <div class="films">
    <ul class="py-2" v-for="element in film" :key="`filmID-${element.id}`">
      <li>
        <h2>Title: {{element.title}}</h2>
      </li>
      <li>
        <h4>Original title: {{ element.original_title }}</h4>
      </li>
      <li>
        <img v-if="element.original_language ==='it'" src="../assets/it.png" alt="element.original_language">
        <img v-else-if="element.original_language === 'en'" src="../assets/en.png" alt="element.original_language">
        <p v-else>Language: {{ element.original_language }}</p>
      </li>
      <li>
        <p>Vote: {{ element.vote_average }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
    name: 'Mainer',
    props: {
      film: Array,
    },
    data() {
      return {

      }
    }
}
</script>

<style scoped lang="scss">
  img{
  width: 20px;
  border-radius: 50%;
}
</style>