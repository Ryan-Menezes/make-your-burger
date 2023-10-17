<template>
  <div>
    <form id="burger-form">
      <div class="input-container">
        <label for="nome">Nome do cliente:</label>
        <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome" />
      </div>
      <div class="input-container">
        <label for="pao">Escolha o pão:</label>
        <select id="pao" name="pao" v-model="pao">
          <option value="">Selecione o seu pão</option>
          <option value="integral">Integral</option>
        </select>
      </div>
      <div class="input-container">
        <label for="carne">Escolha a carne do seu burger:</label>
        <select id="carne" name="carne" v-model="carne">
          <option value="">Selecione o tipo de carne</option>
          <option value="maminha">Maminha</option>
        </select>
      </div>
      <div class="input-container" id="opcionais-container">
        <label for="opcionais" id="opcionais-title">Selecione os opcionais:</label>
        <div class="checkbox-container">
          <input type="checkbox" name="opcionais[]" id="salame" v-model="opcionais" value="salame" />
          <label for="salame">Salame</label>
        </div>
      </div>
      <div class="input-container">
        <input type="submit" class="submit-btn" value="Criar meu Burger" />
      </div>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'BurgerForm'
  }
</script>

<style scoped>
  #burger-form {
    max-width: 600px;
    margin: 0 auto;
  }

  .input-container {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
  }

  label {
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;
    padding: 5px 10px;
    border-left: 4px solid #FCBA03;
  }

  input, select {
    padding: 15px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }

  input:focus, select:focus {
    outline: 1px solid #FCBA03;
  }

  #opcionais-container {
    flex-direction: row;
    flex-wrap: wrap;
  }

  #opcionais-container #opcionais-title {
    width: 100%;
  }

  #opcionais-container .checkbox-container {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
    width: 25%;
  }

  #opcionais-container .checkbox-container label {
    border: none;
    margin: 0;
  }

  .submit-btn {
    background-color: #222;
    color: #FCBA03;
    font-weight: bold;
    padding: 20px;
    cursor: pointer;
    font-size: 16px;
    transition: .5s;
  }

  .submit-btn:hover {
    background-color: #FCBA03;
    color: #222;
  }
</style>
