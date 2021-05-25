<template>
  <form class="d-flex mt-3 mb-3">
    <div class="flex-grow-1">
      <!-- searchArt è la stringa di ricerca che inizialmente come dichiarato in data sarà vuota  -->
     <input v-model.trim='searchArt' @keyup.enter='startSearch' class="form-control" type="text" placeholder="Cerca  Artista"> 
    </div>
    <div class="ms-3">
      
      <button @click.prevent='startSearch' class="btn btn-primary"> 
        Cerca
      </button>
    </div>
    <div class="ms-3">
      
      <button @click.prevent='resetSearch' class="btn btn-warning"> 
        Reset
      </button>
    </div>
  </form>
</template>

<script>

export default {
  name: 'Search',



  data(){
    return {
      searchArt:""
    }
  },

  methods:{
    //questa funzione genererà il nostro evento, la inseriamo nel keyup e nel click
    startSearch(){
      this.$emit("searchCharacter" , this.searchArt )
    }, 

    resetSearch(){
      this.searchArt = "",
      this.startSearch()
    }

  }

  
}
</script>

<style lang='scss' scoped>
  input {
    &:focus {
      box-shadow:  0px 3px 8px #808080;
    }
  }
</style>