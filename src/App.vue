<template>
    <div class="container">
        <app-header></app-header>

        <div class="row">
            <app-foods></app-foods>
        </div>
        <hr>
        <app-footer></app-footer>
    </div>
</template>

<script>
    import Header from './components/Shared/Header.vue';
    import Footer from './components/Shared/Footer.vue';
    import Foods from './components/Food/Foods.vue';

    export default {
        components: {
            'app-header': Header,
            'app-footer': Footer,
            'app-foods': Foods
        }
    }
</script>

<style>

</style>
