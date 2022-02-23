<template>

    <header class="my_header">

        <div class="container-fluid p-0">
            
            <div class=" my_navbar">
                
                <a class="navbar-brand my_style-brand" href="#">
                    <img :src="img" alt="soundcloud-img" width="100" height="50">
                </a>

            </div>

        </div>

    </header>
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

.my_header{
    background-color: #323d48;
}

</style>