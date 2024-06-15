<script setup>

import AppHeader from './components/AppHeader.vue';

</script>

<script>

export default {
  // Properties returned from data() become reactive state
  // and will be exposed on `this`.
  data() {
    return {
      films: [
        {
          titolo: 'Il re leone',
          titoloOriginale: 'The lion king',
          lingua: 'Italiano',
          voto: '7.5326871',
        }
      ],
      index: 0,
    }
  },

  // Methods are functions that mutate state and trigger updates.
  // They can be bound as event handlers in templates.
  methods: {

  },

  // Lifecycle hooks are called at different stages
  // of a component's lifecycle.
  // This function will be called when the component is mounted.
  mounted() {
    console.log(this.films.titolo)
  }
}

</script>

<template>

  <AppHeader/>
  <main>

    <section>
      <input type="text" name="searchbar" id="searchbar">
      <button>Invia</button>
    </section>

    <div>
      <ul v-if="films" >
        <li>Titolo: {{ films[index].titolo }}</li>
        <li>Titolo Originale: {{ films[index].titoloOriginale }}</li>
        <li>Lingua: {{ films[index].lingua }}</li>
        <li>Voto: {{ parseInt(Number(films[index].voto)) }}</li>
      </ul>
    </div>

  </main>

</template>

<style lang="scss">
@use './styles/general.scss';
@use './styles/partials/mixin';
@use './styles/partials/variants';

section{
  margin-left: 1.5rem;
}

ul{
  margin-left: 2rem;

  li{
    list-style: none
  }
}
</style>
