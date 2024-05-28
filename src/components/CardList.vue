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
            cardLink: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?cardset=metal%20raiders&num=20&offset=0',
        }
    },
    methods: {
    },
    mounted() {
        axios.get(this.cardLink).then((elemento) => {
            this.store.cards = elemento.data.data
        });
    }

}
</script>

<template>
    <div class="contenitore">
        <div class="founded-card">
            <h3>Found {{ store.cards.length }} Card</h3>
        </div>
        <div class="card-container">

            <SingleCard v-for="card in store.cards" :description="card.name" :model="card.type"
                :img="card.card_images[0].image_url" />

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
}
</style>