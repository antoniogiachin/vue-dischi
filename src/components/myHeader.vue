<template>

    <header class="my_header">

        <div class="container-fluid p-0">
            
            <div class=" my_navbar d-flex align-items-center justify-content-between pe-2 ">
                
                <a class="navbar-brand my_style-brand" href="#">
                    <img :src="img" alt="soundcloud-img" width="100" height="50">
                </a>

                <select name="genre-select" id="genre" class="float-end d-inline-block" v-model="valueGenre" @change="getValueGenre()">
                    <option value="">Seleziona il genere musicale</option>
                    <option v-for="(genre, index) in vinylGenreCopy " :key="index" :value="genre" >{{genre}}</option>
                </select>

                <select name="genre-select" id="genre" class="float-end d-inline-block" v-model="valueAuthor" @change="getAuthorGenre()">
                    <option value="">Seleziona l'artista</option>
                    <option v-for="(author, index) in vinylAuthorsCopy " :key="index" :value="author">{{author}}</option>
                </select>

            </div>

        </div>

    </header>
</template>

<script>
export default {
    name: 'myHeader',

    data(){
        return{
            img: require("../assets/soundcloud.png"),

            //variabile genere stringa
            valueGenre: '',

            // variabile author stringa
            valueAuthor: '',
        }
    },

    methods: {

        // lancio funzione al change e creo ascoltatore con emit per genere
        getValueGenre(){
            this.$emit('valoreGenereCorrente', this.valueGenre)
        },

        // lancio funzione al change e creo ascoltatore con emit per autore
        getAuthorGenre(){
            this.$emit('valoreAutoreCorrente', this.valueAuthor)
        },
        
    },

    props: {

        "vinylGenreCopy" : Array,

        "vinylAuthorsCopy" : Array,

    },
}
</script>

<style lang="scss" scoped>

.my_header{
    background-color: #323d48;
}

</style>