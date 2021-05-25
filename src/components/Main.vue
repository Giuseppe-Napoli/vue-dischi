<template>
  <div class="container wrap">
     <div 
     v-if="!loading"
     class="row d-flex justify-content-center">
      <Search  @searchCharacter = 'searching'/>
      <searchGeneral @searchGen = 'search'
      :genres="genres"/>
      <Album 
      v-for="(album,index) in filteredSong" 
      :key="index"
      :album= "album"
      />
     <div class="text-center">
       <h3>Numero album: {{filteredSong.length}}</h3>
     </div>
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
import Search from '@/components/Search'
import searchGeneral from '@/components/searchGener'

export default {
  name: 'Main',

  components: {
    Album,
    Loader,
    Search,
    searchGeneral
  },

  data(){
    return {
      axios,
      albums:[],
      genres:[],
      loading: true,
      textToSearch:'',
      genSelect: '1'
      
    }
  },

  methods:{
    searching(text){
      this.textToSearch = text;
    },
    search(gen){
      this.genSelect = gen ;
    }
  },
  computed:{
    filteredAlbums(){
      return this.albums.filter(item => item.author.toLowerCase().includes(this.textToSearch.toLowerCase()))
    },
    filteredSong(){
      if(this.genSelect === '1'){
        return this.albums
      }
      return this.albums.filter(item => item.genre.includes(this.genSelect))
    }
  },

  created(){

    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res=>{
      console.log(res.data.response);
      this.albums = res.data.response
      this.albums.forEach((album)=>{
        if(!this.genres.includes(album.genre)){
        this.genres.push(album.genre)
        }
      })
      this.loading = false
    })
    .catch(err=>{
      console.log(err);
    })
  },
}
</script>

<style  lang="scss" scoped>
  div{
    h3{
      color: white;
    }
  }
</style>