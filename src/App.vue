<template>
  <div id="app">
    <myHeader :vinylGenreCopy="vinylGenreCopy" :vinylAuthorsCopy="vinylAuthorsCopy"/>
    <myMain @arrayGeneri="copiaGeneri" @arrayAutori="copiaAutori"/>
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

      vinylGenreCopy: [],

      vinylAuthorsCopy: [],

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
    }

  },

}
</script>

<style lang="scss">
  @import "./assets/style/general.scss";
</style>
