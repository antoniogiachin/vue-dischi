<template>
    <main class="">
        <div class="container">
            <div class="row">
                <div class="col" v-for="(vinyl,index) in vinylArrayObj" :key="index">
                
                </div>
            </div>
        </div>
    </main>
</template>

<script>
// Integro axios
const axios = require('axios');

export default {
    name:'myMain',

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

}

.my_card{
    background-color: #323d48;
}

</style>