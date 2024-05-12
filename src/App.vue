<script>
import { store } from "./store"
import axios from "axios";
import AppHeader from './components/AppHeader.vue';
import AppCards from "./components/AppCards.vue";
import SpinnerComponent from "./components/SpinnerComponent.vue"
import AppSearch from "./components/AppSearch.vue"

export default {
  components: {
    AppHeader,
    AppCards,
    SpinnerComponent,
    AppSearch,
  },

  data() {
    return {
      store,
      isReady: false,
      counterValue: "",
    };
  },

  created() {
    this.getCard();
  },

  methods: {
    getCard() {
      this.isReady = false
      const param = {
        status: "All"
      }

      if (this.store.selectedStatus !== "All") {
        param.status = this.store.selectedStatus;

        axios.get("https://rickandmortyapi.com/api/character", {
          params: param,
        }).then((resp) => {
          this.counterValue = resp.data.info.count
          this.store.charactersArray = resp.data.results
          this.isReady = true
        });
      } else {
        axios.get("https://rickandmortyapi.com/api/character").then((resp) => {
          this.counterValue = resp.data.info.count
          this.store.charactersArray = resp.data.results
          this.isReady = true
        });
      }
    }
  }
}
</script>

<template>
  <AppHeader />
  <div class="container">
    <div class="row">
      <SpinnerComponent v-if="!isReady" />
      <AppSearch @filter="getCard" :counter="counterValue" />
      <AppCards v-if="isReady" :charactersArray="store.charactersArray" />
    </div>
  </div>
</template>

<style>

</style>
