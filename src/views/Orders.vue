<template>
  <main class="main-container">
    <h1>Gerenciar Pedidos</h1>
    <Dashboard />
  </main>
</template>

<script>
  import Dashboard from '@/components/Dashboard.vue'

  export default {
    name: 'Orders',
    components: {
      Dashboard
    }
  }
</script>

