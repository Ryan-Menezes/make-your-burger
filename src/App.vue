<template>
  <Navbar />
  <RouterView />
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
    }
  }
</script>
