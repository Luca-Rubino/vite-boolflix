<script>

export default {
  // Properties returned from data() become reactive state
  // and will be exposed on `this`.
    data() {
        return {
            
        }
    },

    props:{
      filmLista: {
            
        },
    },

  // Methods are functions that mutate state and trigger updates.
  // They can be bound as event handlers in templates.
    methods: {},
    created() {},

    // Lifecycle hooks are called at different stages
    // of a component's lifecycle.
    // This function will be called when the component is mounted.
    mounted() {
      console.log(this.filmLista)
    }
}

</script>

<template>
      <div>
        <ul v-for="(filmLista, page) in filmLista" :key="page">
          <li>
            <img :src="`https://image.tmdb.org/t/p/original${filmLista.poster_path}`" :alt="filmLista.title">
          </li>
          <li>Titolo: {{ filmLista.title }}</li>
          <li>Titolo Originale: {{ filmLista.original_title }}</li>
          <li>Lingua:<!--{{ filmLista.original_language }}-->&nbsp;
            <img src="../assets/img/us.jpg" alt="us-flag">
          </li>
          <li>Voto: {{ parseInt(Number(filmLista.vote_average)) }}
            <i v-for="i in (Math.floor(filmLista.vote_average / 2))" class="fa-solid fa-star my-color-yellow"></i>
            <i v-for="i in (5 - Math.floor(filmLista.vote_average / 2))" class="fa-regular fa-star"></i>
          </li>
        </ul>
      </div>
</template>

<style lang="scss">
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

      li:nth-of-type(1) {
        img {
          width: 25rem;
          height: 35rem;
          border-radius: 25px;
          position: relative;
        }
      }

      li {
        list-style: none;
        margin-bottom: .5rem;

        img {
          width: 25px;
          height: 15px;
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