<script>
import SingleCard from './SingleCard.vue';
import store from '../data/store.js'

export default {
    components: {
        SingleCard
    },

    data() {
        return {
            store,
        }
    },
    methods: {
    },
    mounted() {

    }

}
</script>

<template>
    <div class="contenitore">
        <div class="founded-card">
            <h3 v-if="store.cards.length > 0">Found {{ store.cards.length }} Card</h3>
        </div>
        <div class="card-container">

            <SingleCard v-for="card in store.cards" v-if="store.cards.archetype == store.sceltaInput"
                :description="card.name" :model="card.archetype" :img="card.card_images[0].image_url" />

        </div>

    </div>


</template>

<style scoped>
.contenitore {
    width: 80%;
    margin: 0 auto;
    min-height: 10rem;
    background-color: white;
    padding: 3rem;
}

.founded-card {
    height: 3rem;
    background-color: #222;
    color: white;
    align-content: center;
    padding: 0.8rem;
}

.card-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    width: 100%;
    gap: 1rem;
}
</style>