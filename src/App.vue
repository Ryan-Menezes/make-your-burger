<template>
  <Navbar :logo="logoSrc" :alt="appName" />

  <main class="main-container">
    <RouterView />
  </main>

  <Footer />
</template>

<script>
  import { RouterView } from 'vue-router'
  import Navbar from '@/components/Navbar.vue'
  import Footer from '@/components/Footer.vue'

  export default {
    name: 'App',
    components: {
      RouterView,
      Navbar,
      Footer
    },
    data() {
      return {
        appName: 'Make your burger',
        logoSrc: '/img/logo.png'
      }
    }
  }
</script>

<style>
  * {
    font-family: Helvetica, sans-serif;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  .main-container {
    margin: 50px;
    min-height: 60vh;
  }

  h1 {
    text-align: center;
    font-size: 42px;
    margin-bottom: 30px;
    color: #222;
  }
</style>
