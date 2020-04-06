<template>
  <div class="detail-container" v-if="film" id="filmDetailerContainer">
      <h2>{{film.title}}</h2>
      <p><span>Description:</span>{{film.description}}</p>
      <p><span>Director:</span>{{film.director}}</p>
      <p><span>Rating:</span>{{film.rt_score}}</p>
  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
    name:'film-detail',
    data(){
        return {
            film: null
        }
    },
    mounted(){
        eventBus.$on('film-selected', (film) => {
            this.film = film
        })
    }

}
</script>

<style>
.detail-container {position: relative;
                    border: white 1%;
                    border-style: double;
                    background-color: powderblue;
                    color: white;
                    padding: 1.5%;
                    margin: 0.5%;}
</style>