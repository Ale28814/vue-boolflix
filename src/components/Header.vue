<template>
  <div class="bgc p-2">
      <input type="text" placeholder="Inizia ricerca" v-model="BarText" @keyup.enter="$emit('searchClick', BarText)">
      <button @click="$emit('searchClick', BarText)">Cerca</button>
  </div>
</template>

<script>
export default {
    name: 'Header',
    data() {
      return {
        BarText: '',
      }
    }
}
</script>

<style scoped lang="scss">
  .bgc{
     background-image: linear-gradient(45deg, green, white, red);
  }
</style>