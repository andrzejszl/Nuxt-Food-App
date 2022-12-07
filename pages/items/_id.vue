<template>
    <main class="container">
        <section class="image" :style="`background: url(/${currentItem.img}) no-repeat center center`"></section>
        <section class="details">
            <h3>Description</h3>
            <div>
                {{ currentItem.description }}
            </div>
        </section>
        <section class="options">
            <div class="order">
                <h2>{{ currentItem.item }}</h2>
                <h3>Price: ${{ currentItem.price }}</h3>
                <input type="number" name="count" id="count" v-model="count" min="1">
                <label for="count"></label>
                <button @click="addToCart">Add to Cart - ${{ itemsPrice }}</button>
            </div>
            <div v-if="currentItem.options" class="options--options">
                <fieldset>
                    <legend>Options:</legend>
                    <div class="option" v-for="element in currentItem.options">
                        <input type="radio" :id="element" :name="element" :value="element" v-model="itemOptions">
                        <label :for="element" :key="element">{{ element }}</label>
                    </div>
                </fieldset>
            </div>
            <div v-if="currentItem.addOns" class="options--addOns">
                <fieldset>
                    <legend>Add Ons:</legend>
                    <div class="option" v-for="element in currentItem.addOns">
                        <input type="checkbox" :id="element" :name="element" :value="element" v-model="itemAddons">
                        <label :for="element" :key="element">{{ element }}</label>
                    </div>
                </fieldset>
            </div>
            <AppToast v-if="cartSubmitted">Order submitted!<br>Check out more <nuxt-link to="/restaurants">restaurants!</nuxt-link></AppToast>
        </section>
    </main>
</template>

<script>
import { mapState } from 'vuex';
import AppToast from '@/components/AppToast.vue';

    export default {
        components: {
            AppToast
        },
        data() {
            return {
                id: this.$route.params.id,
                count: 1,
                itemOptions: '',
                itemAddons: [],
                itemSizeAndCost: [],
                cartSubmitted: false,
            }
        },
        computed: {
        ...mapState([
            'fooddata',
        ]),
        currentItem() {
            let result

            for (let i = 0; i < this.fooddata.length; i++) {
                for (let j = 0; j < this.fooddata[i].menu.length; j++) {
                    if (this.fooddata[i].menu[j].id === this.id) {
                        result = this.fooddata[i].menu[j]
                        break
                    }
                }
            }
            
            return result
        },
        itemsPrice() {
            return (this.count * this.currentItem.price).toFixed(2)
        }
    },
    methods: {
        addToCart() {
            let formOutput = {
                item: this.currentItem,
                count: this.count,
                options: this.itemOptions,
                addons: this.itemAddons,
                combinedPrice: this.itemsPrice
            }
            this.cartSubmitted = true
        }
    }
    }
</script>

<style lang="scss" scoped>
.container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 50px;
    margin: 100px auto;
    max-width: 1240px;
    .image {
        width: 640px;
        margin: 0 50px 50px 0;
    }
    .options {
        position: relative;
        grid-column-start: 2;
        grid-row-start: 1;
        width: 400px;
        .toast {
            position: absolute;
            bottom: 110%;
            top: auto;
            left: 0;
            right: auto;
        }
        .order {
            h2 {
                font-size: 2rem;
            }
            h3 {
                margin: 20px 0;
            }
            input#count {
                width: 50px;
                font-size: 1.5rem;
            }
        }
    }
    .details {
        grid-column-start: 1;
    }
}
</style>