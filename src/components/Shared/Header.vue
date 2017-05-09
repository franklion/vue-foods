<template>
    <div class="row">
        <div class="col-xs-12">
            <header class="col-xs-12 page-header">
                <img :src="img" class="app-logo">
                <h1 class="app-title">My Food List</h1>
                <div class="app-fireworks"></div>
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

<style lang="css">
    .page-header {
        position: relative;
    }

    .app-title {
        line-height: 58px;
        text-align: center;
    }

    .app-logo {
        position: absolute;
        left: 0;
        top: 0;
        display: block;
        width: 100px;
        height: auto;
    }

    .app-fireworks {
        position: absolute;
        right: 0;
        top: 0;
        width: 100px;
        height: 100px;
        background-size: cover;
        background-image: url("../../assets/images/fireworks.png");
        background-repeat: no-repeat;
    }

    @media screen and (max-width: 500px) {
        .app-title {
            font-size: 28px;
            line-height: 24px;
        }

        .app-logo {
            width: 60px;
        }

        .app-fireworks {
            width: 60px;
            height: 60px;
        }
    }
</style>
