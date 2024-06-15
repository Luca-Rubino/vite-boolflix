<script setup>

import AppHeader from './components/AppHeader.vue';

</script>

<template>

  <AppHeader/>
  <main>
    <input type="text" name="searchbar" id="searchbar">
    <button>Invia</button>

    <div>
      <ul>
        <li>Titolo</li>
        <li>Titolo Originale</li>
        <li>Lingua</li>
        <li>Voto</li>
      </ul>
    </div>

  </main>

</template>

<style lang="scss">
@use './styles/general.scss' as *;
@use './styles/partials/mixin' as *;
@use './styles/partials/variants' as *;

ul{
  margin-left: 2rem;

  li{
    list-style: none
  }
}
</style>
