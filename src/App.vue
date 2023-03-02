<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from "axios";
import { store } from "./assets/store";

export default {
  data() {
    return {
      store,
      endPoint: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=15&offset=0",
    }
  },

  components: { AppHeader, AppMain },

  created() {
    axios.get(this.endPoint).then((response) => {
      store.cards = response.data.data;
    })
  },

  methods: {
    cardsTypeToSearch(typeChoose) {
      console.log(typeChoose);
      this.endPoint += "?type=" + typeChoose;
      console.log(this.endPoint);
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
