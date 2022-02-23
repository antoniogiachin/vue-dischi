<template>

  <div class="my_card">
        <div class="my_card-img">
            <img :src="vinyl.poster" alt="vinyl-poster">
        </div>
        <div class="my_card-text text-center">
            <h6 class="text-white text-uppercase">{{vinyl.title}}</h6>
            <span class="text-secondary d-block">{{vinyl.author}}</span>
            <span class="text-secondary">{{vinyl.year}}</span>
        </div>
    </div>

</template>

<script>
export default {
    main: 'myCard',

    props: {

        'vinyl' : Object,
        
    }
}
</script>

<style lang="scss" scoped>

.my_card{
    background-color: #323d48;
    height: 350px;
    margin-bottom: 20px;
    padding: 20px;

    .my_card-img{
        height: 50%;
        margin-bottom: 20px;

        img{
            width: 100%;
            height: 100%;
            object-fit: contain;
        }
    }

    .my_card-text{
        height: 50%;
    }
}

</style>