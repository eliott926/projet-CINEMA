<template>
  <div className="recherche">
    <form v-on:submit.prevent="recherche()">
      <div className="input-group">
        <input type="text" placeholder="Que recherchez-vous ?" v-model="uneRecherche">
        <button class="button1" v-on:click="recherche ">Rechercher</button>
      </div>
    </form>
    <h2>Resultats de la recherche</h2>
    <table>
      <tr v-for="unFilm in films" v-bind:key="unFilm.key">
        <td v-if="unFilm.poster_path!=null" width="400px">
        <td>{{unFilm.title}}</td>
          <img v-bind:src="'http://image.tmdb.org/t/p/w500' + unFilm.poster_path"></td>
        <td>
         <button class="button" v-on:click="voirDetails(unFilm)">Détails</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
  import axios from 'axios'
  
  export default {
    name: 'Recherche ',
    data() {
      return {
        baseUrl: 'https://api.themoviedb.org/3/search/movie' ,
        films: [],

        uneRecherche: '',
        api_key: '3f2e73f99471592447bae321c22cd045'
      }
    },
    methods: {
      async recherche(){
        // const response = await axios.get(this.baseUrl + '/search.json?title=${this.query}');
        const response = await axios.get(this.baseUrl + '?api_key=' + this.api_key + '&query=' + this.uneRecherche);
        this.films = await response.data.results;
      },

      voirDetails(film) {
        this.$router.push({
          path: 'details', query: {
            id: film.id,
            titre: film.title
          }
        });
      }
    }
  }
</script>


<style lang ="scss">

h2 {

  padding: 20px;
  font-size: 19px;
}


.button {
  width: 100%;
  padding: 15px 100px;
  margin: 10px 4px;
  color: #FFFFFF;
  background-color: mediumvioletred;
  font-family: sans-serif;
  text-transform: uppercase;
  text-align: center;
  position: relative;
  right: -80px;
  bottom: -270px;
  text-decoration: none;
  display: inline-block;
  border: 1px solid;



}

.button1{
  padding: 15px 100px;
  margin: 10px 4px;
  color: #FFFFFF;
  background-color: mediumvioletred;
  font-family: sans-serif;
  text-transform: uppercase;
  text-align: center;
  position: relative;
  right: 0px;
  bottom:-30px;
  text-decoration: none;
  display: inline-block;
  border: 1px solid;



}

.input-group {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 16px;
}

input{
  display: inline-block;
  appearance: none;
  border: none;
  outline: none;
  background: none;
  &[type="text"] {
    width: 100%;
    color: mediumvioletred;
    background-color: #FFFFFF;
    font-size: 30px;
    padding: 10px 16px;
    border-radius: 5px;
    margin-bottom: 6px;
    transition: 0.4s;
    text-transform: capitalize;
    text-align: center;
    width: 390px;
  
  }
}



        
</style>
