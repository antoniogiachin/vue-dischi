<template>
    <main class="my_main">
        <div class="container">
            <div class="row row-cols-lg-5 row-cols-md-3 row-cols-2">
                <div class="col" v-for="(vinyl,index) in vinylArrayObj" :key="index"  >

                    <myCard :vinyl="vinyl" />

                </div>
            </div>
        </div>
    </main>
</template>

<script>
// Integro axios
const axios = require('axios');

import  myCard from './partials/myCard.vue'

export default {
    name:'myMain',

    components :{

        myCard,

    },

    data(){

        return{
            vinylArrayObj: [],
        }

    },

    methods : {
        //methodo da lanciare alla creazione app vue per ricevere dal server l'array di obj
        getArrayObj(){
           axios.get('https://flynn.boolean.careers/exercises/api/array/music')
           //Arrow function per usare il this
            .then((response) => {
                // handle success
                this.vinylArrayObj = response.data.response;
                console.log(this.vinylArrayObj)
                console.log(response);
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
            .then(function () {
                // always executed
            }); 
        }
    },

    created(){
        this.getArrayObj()
    }
}
</script>

<style lang="scss" scoped>

.my_main{
    background-color: #23313d;
    display: flex;
    align-items: center;
    overflow: scroll;
}

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

@media screen and (min-width: 993px){
    .my_main{
        height: calc(100vh - 50px);
    }
}

</style>