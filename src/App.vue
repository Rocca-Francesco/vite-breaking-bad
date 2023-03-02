<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from "axios";
import { store } from "./assets/store";

export default {
  data() {
    return {
      store,
      // salvo il mio endpoint per le chiamate axios base
      baseEndPoint: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=15&offset=0",

      // inizialmente il mio endpoint sarà uguale a quello base
      newEndPoint: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=15&offset=0",
    }
  },

  components: { AppHeader, AppMain },

  created() {
    axios.get(this.baseEndPoint).then((response) => {
      store.cards = response.data.data;
    })
  },

  methods: {
    generateCards(url) {
      console.log(url);
      axios.get(url).then((response) => {
        store.cards = response.data.data;
      })
    },

    cardsTypeToSearch(typeChoose) {
      // se selezione all type la selezione mostra tutte le carte
      if (typeChoose == "All Type") {
        this.newEndPoint = this.baseEndPoint;
        this.generateCards(this.newEndPoint)
      }
      else {
        this.newEndPoint = this.baseEndPoint;
        this.newEndPoint += "&type=" + typeChoose;
        this.generateCards(this.newEndPoint)
      }
    }
  }
}
</script>

<template>
  <AppHeader />
  <AppMain @searchType="cardsTypeToSearch" />
</template>

<style lang="scss">
@use "./assets/general.scss"
</style>
