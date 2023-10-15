<template>
  <header>
    <nav id="nav">.
      <RouterLink to="/">
        <img src="" alt="" id="logo" />
      </RouterLink>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/pedidos">Pedidos</RouterLink>
    </nav>
  </header>
</template>

<script>
  import { RouterLink } from 'vue-router'

  export default {
    name: 'Navbar',
    components: {
      RouterLink
    }
  }
</script>

<style scoped>

</style>
