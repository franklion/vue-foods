<template>
    <div class="col-xs-12">
        <button class="btn btn-default" @click="shuffle">Shuffle</button>
        <button class="btn btn-default" @click="reset">Reset</button>
        <button class="btn btn-default btn-like" @click="fetchLoveFood" :class="{ 'is-active' : filteredlikeStatus === true}">Love Food</button>
        <button class="btn btn-default btn-like" @click="fetchNormalFood" :class="{ 'is-active' : filteredlikeStatus === false}">Normal Food</button>
        <hr>

        <div class="row">
            <div class="form-group col-md-4">
                <label for="food-name">Search Name:</label>
                <input type="text" class="form-control" id="food-name" v-model="filteredName">
            </div>
        </div>


        <hr>
        <transition-group name="flip-list" tag="ul" class="col-xs-12 col-sm-12 list-group">
            <li
                    class="col-xs-12 col-sm-6 col-md-3 list-group-item"
                    v-for="food in filteredFoods"
                    :key="food.id">

                <div class="item ">
                    <p class="food-title"># {{ food.id }} {{ food.name }}</p>
                    <p class="food-desc">Status :
                        <span
                                class="glyphicon glyphicon-heart-empty love-color"
                                aria-hidden="true"
                                v-if="food.status">
                    </span>
                        <span
                                class="glyphicon glyphicon-grain grain-color"
                                aria-hidden="true"
                                v-else="!food.status">
                    </span>
                    </p>
                    <img class="img-responsive food-image" :src="'src/assets/images/'+ food.img">
                </div>



            </li>
        </transition-group>
    </div>
</template>

<script>

    export default {
        data: function () {
            return {
                foods: [
                    {id: 1, name: "cake", img: "cake.svg", status: true},
                    {id: 2, name: "carrot", img: "carrot.svg", status: false},
                    {id: 3, name: "fish", img: "fish.svg", status: true},
                    {id: 4, name: "grape", img: "grape.svg", status: true},
                    {id: 5, name: "watermelon", img: "watermelon.svg", status: false},
                    {id: 6, name: "juice", img: "juice.svg", status: true},
                    {id: 7, name: "milk", img: "milk.svg", status: true},
                    {id: 8, name: "noodle", img: "noodle.svg", status: false},
                    {id: 9, name: "pizza", img: "pizza.svg", status: false},
                    {id: 10, name: "rice_balls", img: "rice_balls.svg", status: false},
                ],
                filteredlikeStatus: null,
                filteredName: ''
            }
        },
        computed: {
            filteredFoods() {
                return this.foods.filter((food) => {
                   let filteredlikeStatusCondition = this.filteredlikeStatus === null ? true : ( food.status === this.filteredlikeStatus);
                   let filteredNameCondition = this.filteredName === '' ? true : ( food.name.toLowerCase().indexOf( this.filteredName.toLowerCase() ) !== -1 );
                   return  filteredlikeStatusCondition && filteredNameCondition;
                });
            }
        },
        methods: {
            shuffle() {
                this.foods = _.shuffle(this.foods);
            },
            reset() {
                this.filteredlikeStatus = null;
                this.filteredName = '';
                this.foods = _.sortBy(this.foods, ['id']);
            },
            fetchLoveFood() {
                this.filteredlikeStatus = true;
//                this.foods = _.filter(this.foods, { 'status': 1});
            },
            fetchNormalFood() {
                this.filteredlikeStatus = false;
            }
        }
    }
</script>

<style>
    .item {
        padding: 10px;
        border: 1px solid #ddd;
    }
    .btn-like.focus, .btn-like:focus {
        color: inherit;
        background-color: inherit;
        border-color: inherit;
    }

    .btn-like.is-active {
        background-color: #f57f8b;
    }

    .list-group {
        padding-left: inherit;
    }

    .food-title {
        font-size: 26px;
    }

    .food-desc {
        font-size: 18px;
    }

    .food-image {
        padding: 15px;
        max-height: 200px;
        margin: 0 auto;
    }

    .love-color {
        color: #d72717;
    }

    .grain-color {
        color: darkgreen;
    }

    .list-group-item {
        border: none;
        padding: 10px 10px;
        background-color: transparent;
    }

    .flip-list-move {
        transition: transform 1s;
    }

    .flip-list-enter, .flip-list-leave-to {
        opacity: 0;
        transition: all 1s;
    }

    .flip-list-leave-active {
        position: absolute;
    }

</style>
