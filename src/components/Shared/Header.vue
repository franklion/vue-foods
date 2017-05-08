<template>
    <div class="row">
        <div class="col-xs-12">
            <header class="page-header">
                <h1>My Food List</h1>
                <!--<img :src="'../../assets/' + cover ">-->
                <img :src="img">
            </header>
        </div>
    </div>
</template>

<script>
    export default {
        data: function () {
            return {
//                cover : '~assets/logo.png'
                img: require('../../assets/logo.png')
            }
        }
    }
</script>

<style>

</style>
