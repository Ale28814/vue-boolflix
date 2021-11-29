<template>
<div class="app">
<Header @searchClick='choos'/>

<Mainer :film="foundFilm"/>

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
      foundFilm: null,
      selection: '',
    }
  },
  methods: {
    getFilms() {
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: 'ea406b3b6df3538757d7eb19761ffa58',
          query: this.selection,
          language: 'it-IT',
        }
      })
      .then(result => {
        this.foundFilm = result.data.results;
      })
    },
    choos(text) {
      this.selection=text;
      this.getFilms()
    }
  }
}
</script>

<style scoped lang="scss">
</style>
