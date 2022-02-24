<template>
  <div id="app">
    <myHeader @valoreGenereCorrente="genreValue" :vinylGenreCopy="vinylGenreCopy" :vinylAuthorsCopy="vinylAuthorsCopy"/>
    <myMain @arrayGeneri="copiaGeneri" @arrayAutori="copiaAutori" :currentGenreValue="currentGenreValue" :currentAuthorValue="currentAuthorValue"/>
  </div>
</template>

<script>
import myHeader from './components/myHeader.vue'
import myMain from './components/myMain.vue'



export default {
  name: 'App',
  components: {
    myHeader,
    myMain,
  },

  data(){
    return {

      // copia array generi
      vinylGenreCopy: [],

      // copia array autori
      vinylAuthorsCopy: [],

      // stringa valore genere corrente
      currentGenreValue: '',

      //stringa valore autore corrente
      currentAuthorValue: '',

    }
  },

  methods: {

    copiaGeneri(array){
      this.vinylGenreCopy = array;
      console.log(this.vinylGenreCopy)
    },

    copiaAutori(array){
      this.vinylAuthorsCopy = array;
      console.log(this.vinylAuthorsCopy)
    },

    // funzione valore genere
    genreValue(value){
      this.currentGenreValue = value;
      console.log(this.currentGenreValue);
    },

    // funzione valore autore
    authorValue(value){
      this.currentAuthorValue = value;
      console.log(this.currentAuthorValue);
    },

  },

}
</script>

<style lang="scss">
  @import "./assets/style/general.scss";
</style>
