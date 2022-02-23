<template>
    <div class="my_load position-absolute top-50 start-50 translate-middle">
        <div class="row" v-if="loadInProgress" >

            <div class="col d-flex justify-content-center">

                <div class="spinner-border me-3 text-white" role="status">
                    <span class="visually-hidden">Loading...</span>
                </div>

                <p class="text-uppercase text-white">caricamento in corso...</p>
            </div>
            
        </div>
    </div>
</template>

<script>
export default {
    name: 'myLoad',

    props:{
        loadInProgress: Boolean,
    }
}
</script>

<style lang="scss" scoped>

</style>