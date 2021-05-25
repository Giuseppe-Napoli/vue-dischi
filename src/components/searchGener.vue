<template>
  <div>
    <select v-model="selected"
    @change="startSearch()">
      <option  value="1">Tutti</option>
      
      <option 
        v-for="(genre, index) in genres" 
        :key="index"
        :value="genre">{{ genre }}
      </option>
    </select>
  </div>
</template>

<script>

export default {
  name: 'searchGeneral',
  props:{
    genres:Array
  },

  data(){

    return{
      selected: '1',
      
    }
  },

  methods:{
    startSearch(){
      this.$emit("searchGen" , this.selected)
    }, 


    
  },

    created(){
      console.log(this.genres);
      
    }
/*   created() {
  
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        res.data.response.forEach((album)=>{
          if(!this.generalArray.includes(album.genre)){
            this.generalArray.push(album.genre)
          }
        })
      })
      .catch((error) => {
        console.log(error);
      });
  }, */
}
</script>

<style>

</style>