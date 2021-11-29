<template>
<div class="app">
<Header/>

    <Mainer/>

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
  methods: {
    getFilms() {
      axios.get('https://api.themoviedb.org/3/movie/550?api_key=faf06f90f56fcb8302b8f361cdab33bb').then(result => {
        return result.data.rersponse
      })
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
