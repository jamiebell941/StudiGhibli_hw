<template>
  <div class="main-container">
    <h1>Studio Ghibli</h1>
    
    <film-filter :films="films" />
    <film-detail />
  </div>
</template>

<script>


import FilmFilter from './components/filmFilter.vue'
import FilmDetail from './components/FilmDetail.vue'

export default {
  name:'app',
  data(){
    return{
      films: [],
      favFilms: []
    };
  },
  components:{
    "film-filter": FilmFilter,
    "film-detail": FilmDetail
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(result => result.json())
    .then(films => this.films = films)
  }

}
</script>

<style scoped>
 .main-container{background-color:antiquewhite;
                font-family: 'Courier New', Courier, monospace;
                color: white;
                border: white;
                padding: 2%;
                margin: 2%;
            }
</style>