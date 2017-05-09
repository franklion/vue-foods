<template>
    <div class="row">
        <div class="col-xs-12">
            <header class="col-xs-12 page-header">
                <img :src="img" class="col-xs-4 app-logo">
                <h1 class="col-xs-6">My Food List</h1>
                <div class="col-xs-2 app-boom"></div>
                <!--<img :src="'../../assets/' + cover ">-->
            </header>
        </div>
    </div>
</template>

<script>
    export default {
        data: function () {
            return {
//                cover : '~assets/logo.png'
                img: require('../../assets/images/cherry.png')
            }
        }
    }
</script>

<style>
    .app-logo {
        display: block;
        width: 100px;
        height: auto;
    }
    .app-boom {
        width: 100px;
        height: 100px;
        border:1px #ccc solid;
        background-image: url("../../assets/images/boom.png");
        background-repeat:no-repeat;
    }
</style>
