<script setup>

import listaTitoli from '../components/listaTitoli.vue';
// import { store } from '../store';
import axios from 'axios';

</script>

<!-- https://api.themoviedb.org/3/discover/movie? -->

<script>

export default {
  // Properties returned from data() become reactive state
  // and will be exposed on `this`.
  data() {
    return {
      films: [
        { titolo: 'Il re leone', titoloOriginale: 'The lion king', lingua: 'Italiano', voto: '9.5326871', img: 'https://pad.mymovies.it/filmclub/2017/04/249/locandina.jpg'},
        { titolo: 'Madagascar', titoloOriginale: 'Madagascar', lingua: 'Italiano', voto: '7.824871', img: 'https://pad.mymovies.it/filmclub/2005/05/064/locandinapg1.jpg'},
      ],
      index: 0,
      // store,
      filmLista: [],
      filtroRicerca: '',
      serieTvLista: [],
    }
  },

  // Methods are functions that mutate state and trigger updates.
  // They can be bound as event handlers in templates.
  methods: {
        //API per elenco i film più richiesti Movies
        getDiscoverMovie(){
          axios.get('https://api.themoviedb.org/3/discover/movie?api_key=68ea9ce68b5006f086ea95c89dbfabe9')
            .then((response) => { 
              this.filmLista = response.data.results;
              console.log(this.filmLista);
            })
            .catch(function(error) {
              console.log(error);
            }
        )},
        getsearchtv(value) {
          this.filtroRicerca = value;
          console.log(this.filtroRicerca)
          axios.get(`https://api.themoviedb.org/3/search/tv?api_key=68ea9ce68b5006f086ea95c89dbfabe9&query=${this.filtroRicerca}`)
          .then((response) => {
              this.serieTvLista=response.data.results;
              console.log(this.serieTvLista)
          })
          .catch(function(error){
              console.log(error);
          })
          .finally(function(){
          });
        },
        created() {
          this.getDiscoverMovie();
          this.getsearchtv();
        },
        },

  // Lifecycle hooks are called at different stages
  // of a component's lifecycle.
  // This function will be called when the component is mounted.
  mounted() {
    console.log(this.films[0].titolo);
    console.log(this.films[1].titolo);
    // console.log(store.apiUrl + store.apiKey + '&language=' + store.lang + '&query=' + store.queryRicerca)
    // richiamo i dati presenti nell'Api e li trasferisco in un arrey vuoto in modo da poterli leggere
    this.getDiscoverMovie();
    this.getsearchtv();
  }
}

</script>

<template>

  <main>

    <section>

      <div>
        <label for="searchbar">Cerca il tuo film:</label>
        <input id="searchbar" type="text" name="searchbar" placeholder="Nome film" @change="getsearchtv(filtroRicerca)" :value="filtroRicerca" @keyup.enter="value">
        <input type="button" value="Cerca"/>
      </div>

      <listaTitoli :filmLista="filmLista" :filtroRicerca="filtroRicerca"/>

      <div>
        <ul v-for="(serieTvLista, page) in serieTvLista" :key="page">
          <li>
            <img :src="`https://image.tmdb.org/t/p/original${serieTvLista.poster_path}`" :alt="serieTvLista.title">
          </li>
          <li>Titolo: {{ serieTvLista.title }}</li>
          <li>Titolo Originale: {{ serieTvLista.original_title }}</li>
          <li>Lingua: {{ serieTvLista.original_language }}</li>
          <li>Voto: {{ parseInt(Number(serieTvLista.vote_average)) }}</li>
        </ul>
      </div>

      <!-- Elenco di prova -->
      <!-- <div>
        <ul v-for="(films, index) in films" :key="index">
          <li>
            <img :src="films.img" :alt="films.titolo">
          </li>
          <li>Titolo: {{ films.titolo }}</li>
          <li>Titolo Originale: {{ films.titoloOriginale }}</li>
          <li>Lingua: {{ films.lingua }}</li>
          <li>Voto: {{ parseInt(Number(films.voto)) }}</li>
        </ul>
      </div> -->

    </section>

  </main>

</template>

<style lang="scss" scoped>
@use '../styles/partials/mixin' as *;

section {
  div {
    @include margin-min;
    display: flex;
    flex-wrap: wrap;

    label {
      margin-right: .3rem
    }
  }
  ul {
    @include margin-min;
    width: 25rem;
    padding: .5rem;
    border: 2px solid rgb(215, 198, 6);
    border-radius: 25px;

    li {
      list-style: none;
      margin-bottom: .5rem;

      img {
        width: 25rem;
        height: 35rem;
        border-radius: 25px;
        position: relative;
      }
      img:active {
        bottom: 1px;
        top: 1px;
      }
    }
    li:last-of-type {
      margin-bottom: 0;
    }
  }
}
</style>
