<template>
  <div class="filter-container">
      <h1>Selet a film!</h1>
        <div class="img-reel">
          <img src="../assets/sgbanner.jpg" width=100%>
        </div>
      
      <form v-on:submit.prevent>
          <!-- <input type="text" v-model="search" placeholder="search for film..." v-on:keyup="searchForFilm"> -->
          <select v-on:change="handleSelect" v-model="selectedFilm">
              <option disabled value="">Select a Film...</option>
              <option v-for="(film, index) in films" :value="film" :key="index">{{film.title}}</option>
          </select>
      </form>
        
  </div>
</template>

<script>
    import {eventBus} from '../main.js'


export default {
    name: 'film-filter',
    data(){
        return {
            "search": "",
            "selectedFilm": {},
        }
    },
    props: ['films'],
    methods: {
        searchForFilm(){
            let foundFilm = this.films.find((film) => {
                return film.toLowerCase().indexOf(this.search.toLowerCase()) > -1
            })
            this.selectedFilm = foundFilm
            
            eventBus.$emit('film-selected', this.selectedFilm)
            },
         handleSelect(){
                this.search = ""
                eventBus.$emit('film-selected', this.selectedFilm)
                            }
    }

}
</script>

<style scoped>
 .filter-container {position: relative;
                    border: white 1%;
                    border-style: double;
                    background-color: powderblue;
                    color: white;
                    padding: 1.5%;
                    margin: 0.5%;
                    align-content: center;}
.search {}
.select {position: relative;
        align-content: center;}

.img-reel{align-content: center;
        width:100%;}
</style>