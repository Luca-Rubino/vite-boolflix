<script>


</script>

<template>

  <header>
    <h1>Vite-boolflix</h1>
  </header>

</template>

<style lang="scss" scoped>
@use '../styles/partials/mixin' as *;

header{
  @include d-flex-center;
  color: darkslateblue;
  background-color: darkcyan;

  h1 {
    padding: 1rem;
  }
}
</style>
