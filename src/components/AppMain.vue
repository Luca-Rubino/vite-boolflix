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
          voto: '9.5326871',
        },
        {
          titolo: 'Madagascar',
          titoloOriginale: 'Madagascar',
          lingua: 'Italiano',
          voto: '7.824871',
        },
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

  <main>

    <section>
      <input type="text" name="searchbar" id="searchbar">
      <button>Invia</button>
    </section>

    <div>
      <ul v-for="(films, index) in films" :key="index" v-show="films">
        <li>Titolo: {{ films.titolo }}</li>
        <li>Titolo Originale: {{ films.titoloOriginale }}</li>
        <li>Lingua: {{ films.lingua }}</li>
        <li>Voto: {{ parseInt(Number(films.voto)) }}</li>
      </ul>
    </div>

  </main>

</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as *;
@use '../styles/partials/mixin' as *;
@use '../styles/partials/variants' as *;

section{
  @include margin-min;
}

ul{
  @include margin-min;

  li{
    list-style: none
  }
}

</style>
