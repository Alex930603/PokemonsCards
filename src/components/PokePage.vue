

<template> 
    <button @click=onGet() > FETCH </button>

    <h1 v-if="message" class="utility-info"> Clicca sulla card per avere più informazioni</h1>

    <div class="pokemon-container">
      <vue-flip active-click class="pokemon-container_single-pokemon" v-for="pokemon in pokeArray">

          <template v-slot:front>

            <div class="pokemon-container_single-pokemon--pokemon-id">          
              <h1>N°{{ pokemon.id }},{{ pokemon.name.english }}</h1>
            </div>

          <div class="pokemon-container_single-pokemon--pic-container">
              <img class="pokemon-pic" :src="pokemon.image.sprite" href={{id}}/>
            </div>

            <div class="pokemon-container_single-pokemon--description">
              <h1>{{ pokemon.description }}</h1>
            </div>

        </template>

        <template v-slot:back>
          <div class="pokemon-container_single-pokemon--pokemon-id">          
              <h1>N°{{ pokemon.id }},{{ pokemon.name.english }}</h1>
            </div>

          <div class="pokemon-container_single-pokemon--pic-container">
              <img class="pokemon-pic" :src="pokemon.image.sprite" href={{id}}/>
            </div>

            <div class="pokemon-container_single-pokemon--moves">
              <h2>Attack : {{ pokemon.base.Attack}}</h2>
              <h2>Defense : {{ pokemon.base.Defense }}</h2>
              <h2>HP : {{ pokemon.base.HP }}</h2>
              <h2>Sp.Attack : {{ pokemon.base["Sp. Attack"]}}</h2>
              <h2>Sp.Defense : {{ pokemon.base["Sp. Defense"]}}</h2>
              <h2>Speed : {{ pokemon.base.Speed }}</h2>
            </div>
        </template>

      </vue-flip>      
    </div>
    


</template>

<script>

import {VueFlip} from "vue-flip"
import axios from 'axios'
import "./../assets/main.scss"
export default {

  components: {
    'vue-flip': VueFlip
  },
  data(){ 

    var message = false;

    return{
            pokeArray:[]
          }
        },

    methods:{
      onGet(){
      
        this.message=true;
        axios
        
        .get("https://api.pikaserve.xyz/pokemon/all/",{})
        .then((response)=>{

          this.pokeArray=(response.data.slice(0,151))
          

        })
        .catch((errors)=>{
          console.log(errors)
        })
      }
    },
   }
  
   
</script>