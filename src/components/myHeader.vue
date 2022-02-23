<template>
  <div class="container-fluid">
    
    <div class="navbar my_navbar">
        
        <a class="navbar-brand my_style-brand" href="#">
        <img :src="img" alt="soundcloud-img" width="100" height="50">
        </a>

    </div>

  </div>
</template>

<script>
export default {
    name: 'myHeader',

    data(){
        return{
            img: require("../assets/soundcloud.png")
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/style/general.scss";

.my_navbar{
    background-color: #323d48;
}
</style>