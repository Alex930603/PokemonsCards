

<template>
  <div class="main-container">
    <PokePage/>
  </div>

</template>

<script>

import PokePage from './components/pokePage.vue';
import "./assets/main.scss";

  export default {
    data() {
        return {
        };
    },
      
    components: { PokePage }
     
  }

</script>
