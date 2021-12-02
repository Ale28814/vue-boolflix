<template>
  <div id="app">
    <Header @searchClick='getWatch' />

    <main class="py-3">
      <div v-if="FoundFilm.length != 0 && FoundSerie.length != 0">
        <!-- Film section -->
        <Mainer 
        :Result="FoundFilm"
        />

        <Mainer 
        :Result="FoundSerie"
        />
      </div>
      <div v-else class="empty">
        <h2>Scegli un film o una serie dal tuo divano</h2>
      </div>
    </main>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Mainer from './components/Mainer.vue';
export default {
  name: 'App',
  components: {
    Header,
    Mainer,
  },
  data() {
      return {
        FoundFilm: [],
        FoundSerie: [],
      };
  },
  methods: {
    getWatch(text) {
      if (text !== '') {
        const apiParams = {
            api_key: 'ea406b3b6df3538757d7eb19761ffa58',
            query: text,
            language: 'it-IT',
        }
        /* Call API for FILM data */
        axios.get('https://api.themoviedb.org/3/search/movie', {
          params: apiParams,
        })
        .then(result => {
          this.FoundFilm = result.data.results;
  
        })
        .catch(error => console.log(error));
  
        /* Call API for SERIES data */
        axios.get('https://api.themoviedb.org/3/search/tv', {
          params: apiParams,
        })
        .then(result => {
          this.FoundSerie = result.data.results;
  
        })
        .catch(error => console.log(error));
      }
    },
  }
}
</script>

<style lang="scss">
@import '@/styles/Global.scss';
.empty {
    height: 80vh;
    padding: 4rem 0;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    color: #dedede;
}
</style>