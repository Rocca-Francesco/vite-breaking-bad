<script>
import { store } from "../assets/store";
import { typesCards } from "../assets/typesCards";

export default {
  data() {
    return {
      store,
      typesCards,
      typeChoose: '',
    }
  },

  methods: {
    typeChange(typeChoose) {
      this.$emit('searchType', typeChoose);
    }
  }
}
</script>

<template>
  <main>
    <section id="cardsList">
      <div class="container">
        <div class="p-2">
          <select name="cardsType" id="cardsType" v-model="typeChoose" @change="typeChange(typeChoose)">
            <option v-for="types in typesCards" :value="types">{{ types }}</option>
          </select>
        </div>
        <div class="row row-cols-5">
          <div class="cards col text-center" v-for="card in store.cards">
            <img :src="card.card_images[0].image_url" alt="">
            <h3 class="text-light">{{ card.name }}</h3>
            <span>{{ card.type }}</span>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<style lang="scss">
#cardsList {
  background-color: #d48f38;

  .row {
    background-color: white;
  }
}

.cards {
  background-color: #d48f38;

  img {
    width: 100%;
  }

  h3 {
    font-size: 1rem;
  }
}
</style>
