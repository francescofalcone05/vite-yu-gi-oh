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
      cardLink: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=1000&offset=0',
      archeLink: 'https://db.ygoprodeck.com/api/v7/archetypes.php',
      specificArchetype: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=',
      scelta: ''
    }
  },
  methods: {
    getSpecificList() {
      if (this.store.sceltaInput != '') {
        this.scelta = this.store.sceltaInput
        axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=" + this.scelta).then((elemento) => {
          this.store.cards = elemento.data.data
          console.log(elemento.data.data);
        });
      }
      //else if (this.store.sceltaInput == '') {
      //   axios.get(this.archeLink).then((elemento) => {
      //     this.store.archetypeList = elemento.data
      //   });
      //}

    }

  },
  created() {
    axios.get(this.archeLink).then((elemento) => {
      this.store.archetypeList = elemento.data

    });
    axios.get(this.cardLink).then((elemento) => {
      this.store.cards = elemento.data.data
    });
  },
  mounted() {

  },
  computed: {

  },
}
</script>

<template>

  <AppHeader />

  <div class="contenitore-input">

    <select @change="getSpecificList()" v-model="store.sceltaInput" name="" id="">
      <option selected value="">Select your archetype</option>
      <option v-for=" tipo in store.archetypeList">{{ tipo.archetype_name }}</option>
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
