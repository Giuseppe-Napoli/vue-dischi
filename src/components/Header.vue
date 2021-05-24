<template>
  <header>
    <div class="wrap mb-5">
      <div class="logo">
        <img src="../assets/img/logo.png" alt="logo">
      </div>
    </div>
  </header>
</template>

<script>
export default {

  name: 'Header'
}
</script>

<style lang="scss" scoped>
  
  .wrap {
    width: 100%;
    height: 60px;
    background-color:#2E3A46;;
    .logo{
      width: 100px;
      height: 100%;
      padding: 5px;
      text-align: center;
      img {
        height: 90%;
        cursor: pointer;
      }
    }
  }
</style>