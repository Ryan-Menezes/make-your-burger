<template>
  <footer id="footer">
    <p>Make your burger &copy; {{ currentYear }}</p>
  </footer>
</template>

<script>
  export default {
    name: 'Footer',
    data() {
      return {
        currentYear: new Date().getFullYear()
      }
    }
  }
</script>

<style scoped>
  #footer {
    height: 200px;
    background-color: #222;
    border-top: 4px solid #111;
    color: #FCBA03;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    width: 100%;
  }
</style>
