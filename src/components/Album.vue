<template>

  <div class="box col-sm-6 col-md-2 m-3 text-center">
       <img class="mb-3 mt-3" :src="album.poster" :alt="album.title">
       <h3 class="mb-3">{{album.title}}</h3>
       <span class="fw-normal">{{album.author}}</span>
       <span>{{album.year}}</span>
       <h6>{{album.genre}}</h6>
  </div>

</template>

<script>
export default {
name: 'Album',
  props:{
    album: Object
  }
}
</script>

<style lang="scss" scoped>
 .box{
   background-color: #2E3A46;
   height: 370px;
   width: 200px;
   img{
     width: 160px;
   }
   h3{
     color: white;
     font-size: 24px;
     text-transform: uppercase;
   }
   span{
     color: #808080;
     font-size: 18px;
     display: block;
   }
 }
</style>