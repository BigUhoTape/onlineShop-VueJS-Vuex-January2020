<template>
    <div class="v-cart-item">
        <img class="v-cart-item__image" :src=" require('../assets/images/' + cart_item_data.image)" alt="">
        <div class="v-cart-item__info">
            <p>{{ cart_item_data.name }}</p>
            <p>{{ cart_item_data.price }}</p>
            <p>{{ cart_item_data.article }}</p>
        </div>
        <div class="v-cart-item__count">
            <p>Count</p>
            <span>
                <button @click="decrementItem">-</button>
                {{cart_item_data.counter}}
                <button @click="incrementItem">+</button>
            </span>
        </div>
        <button @click="deleteFromCart">Delete</button>
    </div>
</template>

<script>

    export default {
        name: "v-cart-item",
        props: {
            cart_item_data: {
                type: Object,
                default() {
                    return {};
                }
            }
        },
        methods: {
            decrementItem() {
                this.$emit('decrement');
            },
            incrementItem() {
                this.$emit('increment');
            },
            deleteFromCart() {
                this.$emit('deleteFromCart');
            },
        },
        mounted() {
            this.$set(this.cart_item_data, 'counter', 1);
        }
    }
</script>

<style lang="less">
    .v-cart-item {
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: nowrap;
        box-shadow: 0 0 8px 0 #e0e0e0;
        padding: 16px;
        margin-bottom: 16px;
        &__image {
            max-width: 50px;
        }
    }
</style>