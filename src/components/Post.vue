<template>
  <div class="card py-2">
      <ul>
          <li>
              <img v-if="poster != null" :src="`https://image.tmdb.org/t/p/w154/${poster}`" :alt="originalTitle">
              <img v-else class="error-img" src="../assets/404.png" alt="404 Error not found">
            </li>
          <li> <strong>Titolo:</strong> {{ title }}
          </li>
          <li> <strong>Titolo Originale: </strong> {{ originalTitle }}</li>
          <li class="language">
              <strong>Lingua: </strong>
                <img 
                v-if="languageDisp.includes(language)"
                :src="require(`../assets/${language}.png`)" :alt="language"
                />
                <span v-else> {{ language }}</span>
          </li>
          <li><strong>Voto: </strong>{{ vote }} </li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'Post',
    props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,
        poster: String,
    },
    data() {
        return {
            languageDisp: ['it', 'en', 'es', 'fr', 'de',],
        }
    },
    computed: {
        Avai() {
            return this.languageDisp.includes(this.language);
        }
    },
}
</script>

<style scoped lang="scss">
    .card{
        background-color: #0d1117;
        color: white;
    };
    
    ul{
        list-style: none;
        .language{
            img{
                width: 30px;
                border-radius: 50%;
            }
        }
    }
</style>