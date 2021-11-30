<template>
<div class="app">
<Header @searchClick='getFilms'/>
<main>
  <Mainer :film="foundFilm" :serie="foundSerie"/>
</main>


</div>
    
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue';
import Mainer from '@/components/Mainer.vue';

export default {
  name: 'App',
  components: {
    Header,
    Mainer,
  },
  data() {
    return {
      foundFilm: [],
      foundSerie: [],
    }
  },
  methods: {
    getFilms(text) {
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: 'ea406b3b6df3538757d7eb19761ffa58',
          query: text,
          language: 'it-IT',
        }
      })
      .then(result => {
        this.foundFilm = result.data.results;
      })
      .catch(error => console.log(error));

      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: 'ea406b3b6df3538757d7eb19761ffa58',
          query: text,
          language: 'it-IT',
        }
      })
      .then(result => {
        this.foundSerie = result.data.results;
      })
    }
  }
}
</script>

<style scoped lang="scss">

</style>
