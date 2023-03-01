<script>
import { store } from "../assets/store";

export default {
  data() {
    return {
      store,
    }
  },
}
</script>

<template>
  <main>
    <section id="cardsList">
      <div class="container">
        <div class="row row-cols-5">
          <div id="cards" class="col text-center" v-for="card in store.cards">
            <img :src="card.card_images[0].image_url" alt="">
            <h3 class="text-light">{{ card.name }}</h3>
            <span>{{ card.archetype }}</span>
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

#cards {
  background-color: #d48f38;

  img {
    width: 100%;
  }

  h3 {
    font-size: 1rem;
  }
}
</style>
