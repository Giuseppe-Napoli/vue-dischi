<template>
  <div class="container wrap">
     <div 
     v-if="!loading"
     class="row d-flex justify-content-center">

      <Album 
      v-for="(album,index) in albums" 
      :key="index"
      :album= "album"
      />
     </div>
     <Loader
     v-else
     title="Music" />
    </div>
</template>

<script>
import axios from 'axios'
import Album from '@/components/Album'
import Loader from '@/components/Loader'

export default {
  name: 'Main',

  components: {
    Album,
    Loader
  },

  data(){
    return {
      axios,
      albums:[],
      loading: true
      
    }
  },

  created(){

    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res=>{
      console.log(res.data.response);
      this.albums = res.data.response
      this.loading = false
    })
    .catch(err=>{
      console.log(err);
    })
  },
}
</script>

<style  lang="scss" scoped>

</style>