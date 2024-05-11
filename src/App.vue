<script>
import axios from "axios";
import AppHeader from './components/AppHeader.vue';
import AppCards from "./components/AppCards.vue";

export default {
  components: {
    AppHeader,
    AppCards
  },
  
  data () {
    return {
      charactersArray: [],
    };
  },

  created() {
    axios.get("https://rickandmortyapi.com/api/character").then((resp)=> {
      console.log(resp);
      this.charactersArray = resp.data.results
      console.log(this.charactersArray);
    });
  },

}

</script>

<template>
  <AppHeader /> 
  <div class="container">
    <div class="row">
        <AppCards :charactersArray ="charactersArray"/>
    </div>
  </div>

</template>

<style>
  
</style>