<template>
  <header class="py-3">
      <div class="container">
          <div class="row justify-content-between align-items-center">
              <div class="col-4">
                  <div class="logo">
                    <img src="../assets/BoolFlix.png" alt="BoolFlix">
                  </div>
              </div>
              <div class="col-3 d-flex justify-content-between align-items-center">
                    <input type="text" placeholder="Cerca"
                        v-model.trim="Text" @keyup.enter="$emit('searchClick', Text)">
                    <button class="search"
                        @click="$emit('searchClick', Text)"
                    >
                        Cerca
                    </button>
              </div>
          </div>
      </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            Text: '',
        }
    }
}
</script>

<style scoped lang="scss">
header {
    background: linear-gradient(45deg, green, white, red);
    
    input {
        background-color: white;
        border: 2px solid black;
        color: black;
        
    }
    .search{
        background-color: rebeccapurple;
        border: 1px solid #333;
        padding: 3px 15px;
        border-radius: 7px;
        color: #dedede;
        &:hover {
            background-color: dodgerblue;
        }
    }
}
</style>