<template>
  <Banner />
  <main class="main-container">
    <BurgerForm />
  </main>
</template>

<script>
  import Banner from '@/components/Banner.vue';
  import BurgerForm from '@/components/BurgerForm.vue';

  export default {
    name: 'Home',
    components: {
      Banner,
      BurgerForm
    }
  }
</script>

