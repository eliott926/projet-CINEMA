<template>
  <section class="hero is-medium is-link">
    <div class="hero-body">
      <p class="title">
        {{film.titre}}
        <h3>{{film.id}}</h3>

      </p>
      <br>
      <p class="subtitle">
        {{films.overview}}
      </p>
    </div>
  </section>
  <section class="hero is-link">
  <div class="hero-body">
    <h2>Note du film</h2>

    {{films.vote_average}}/10



   <center> <h1> Acteurs </h1></center>

    <div class="content">
      <hr>

      <table>
        <tr v-for="unFilm in cast.cast" v-bind:key="unFilm.key">
          <td>{{unFilm.name}}</td>
          <td v-if="unFilm.profile_path" width="130px">
            <img v-bind:src="'http://image.tmdb.org/t/p/w500' + unFilm.profile_path">

          </td>

        </tr>

      <hr>
      <h1> Equipe Technique </h1>

        <tr v-for="unFilm in cast.crew" v-bind:key="unFilm.key">
          <td>{{unFilm.name}}</td>
          <td v-if="unFilm.profile_path" width="70px">
            <img v-bind:src="'http://image.tmdb.org/t/p/w500' + unFilm.profile_path">
          </td>
        </tr>
      </table>
      </div>
  </div>
</section>
  <div class="details">


  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Details',
  data(){
    return{
      film : [],
      films : [],
      cast: [],

      unDetail: '',
      api_key: '3f2e73f99471592447bae321c22cd045'
    }
  },


  created(){
    this.film = {
      id: this.$route.query.id,
      titre: this.$route.query.titre

    }
    this.recherche();
    this.recherche1();
  },

  methods: {
    async recherche(){
      const response = await axios.get('https://api.themoviedb.org/3/movie/' + this.film.id + '?api_key=' + this.api_key + "&language=fr");
      this.films = await response.data;
    },
    async recherche1(){
      const response = await axios.get('https://api.themoviedb.org/3/movie/' + this.film.id + '/credits?api_key=' + this.api_key + "&language=fr");
      this.cast = await response.data;
    },
  }
}
</script>

<style>

.content {
  display: flex;
  justify-content: center;
}


.hero-body{

  background-color: #35495E;
  background-position: center;
}

h1{
  color: white;
  padding: 80px;
  font-size: 45px;

}
h2 {
  color: white;
  padding: 80px;
  font-size: 30px;
}

</style>