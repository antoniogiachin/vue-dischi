<template>
    <main class="my_main">


        <div class="container position-relative">

            <!-- Component per caricamento in corso -->
            <myLoad :loadInProgress="loadInProgress"/>

            <div class="row row-cols-lg-5 row-cols-md-3 row-cols-2">
                <div class="col" v-for="(vinyl,index) in listVinylFiltered" :key="index" >

                    <!-- component card -->
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
import  myLoad from './partials/myLoad.vue'


export default {
    name:'myMain',

    components :{

        myCard,
        myLoad

    },

    props: {

        "currentGenreValue" : String,

        "currentAuthorValue" : String
    },

    data(){

        return{

            //Array ogetti vinili
            vinylArrayObj: [],

            // boolean caricamento in corso
            loadInProgress: true,

            // array generi
            vinylGenreArray: [],

            // array di artisti
            vinylAuthorsArray: [],
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

                // Creo array di generi
                this.vinylArrayObj.forEach(value =>{
                    if(!this.vinylGenreArray.includes(value.genre)){
                        this.vinylGenreArray.push(value.genre);
                    }
                });

                // creo ascoltatore eventi array generi
                this.$emit('arrayGeneri', this.vinylGenreArray);

                // Creo array artist
                this.vinylArrayObj.forEach(value =>{
                    if(!this.vinylAuthorsArray.includes(value.author)){
                        this.vinylAuthorsArray.push(value.author);
                    }
                })

                // creo ascoltatore eventi array autori
                this.$emit('arrayAutori', this.vinylAuthorsArray);


                // Stop del loading in progress, metto il timeouta 300 millisecondi per farlo vedere
                setTimeout(() => {
                    
                    this.loadInProgress=false;

                }, 300);

                console.log(this.vinylArrayObj);
                console.log(this.vinylGenreArray);
                console.log(this.vinylAuthorsArray);
                console.log(response);
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })

        },

    },

    created(){
        this.getArrayObj();
    },

    computed:{

        // filtro per autore in base al value ricevuto dal padre
        listVinylFiltered(){

            if(this.currentGenreValue == "" ){
                return this.vinylArrayObj
            } else {

                return  this.vinylArrayObj.filter(item =>{
                    return item.genre == (this.currentGenreValue) ||  item.author == (this.currentAuthorValue) ;                
                });

            }
            

        }
    }

}
</script>

<style lang="scss" scoped>

.my_main{
    background-color: #23313d;
    display: flex;
    align-items: center;
    overflow: scroll;
    padding: 20px 0px;
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