<script>
import AppMain from './components/AppMain.vue';
import AppHeader from './components/AppHeader.vue';
import store from './data/store.js';
import axios from 'axios';



export default {
  components: {
    AppHeader,
    AppMain,
  },

  data() {
    return {
      store,
      cardLink: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=100&offset=0',
      archeLink: 'https://db.ygoprodeck.com/api/v7/archetypes.php',
      scelta: '',

    }
  },
  methods: {
    getSelectInput() {
      this.store.sceltaInput = this.scelta
      console.log(this.store.sceltaInput);
      // this.store.filteredList = this.filtraCards
      // console.log(this.store.filteredList);
    }
  },
  created() {
    axios.get(this.cardLink).then((elemento) => {
      this.store.cards = elemento.data.data
    });
    axios.get(this.archeLink).then((elemento) => {
      this.store.archetypeList = elemento.data

    });
  },
  mounted() {

  },
  computed: {
    // filtraCards: function () {
    //   return this.store.cards.filter((elemento) => {
    //     return elemento.archetype.match(this.scelta)
    //   })
    // }
  },
}
</script>

<template>

  <AppHeader />

  <div class="contenitore-input">

    <select @input="getSelectInput()" v-model="scelta" name="" id="">
      <option value="" disabled selected>Select your archetype</option>
      <option v-for=" tipo in store.archetypeList" value="">{{ tipo.archetype_name }}</option>
    </select>

  </div>

  <AppMain />

</template>

<style scoped>
.contenitore-input {
  width: 80%;
  margin: 1rem auto;
}

select {
  width: 20%;
  padding: 0.3rem;
}
</style>
