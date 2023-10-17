<template>
  <div>
    <form id="burger-form" @submit="createBurger">
      <div class="input-container">
        <label for="nome">Nome do cliente:</label>
        <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome" />
      </div>
      <div class="input-container">
        <label for="pao">Escolha o pão:</label>
        <select id="pao" name="pao" v-model="pao">
          <option value="">Selecione o seu pão</option>
          <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
        </select>
      </div>
      <div class="input-container">
        <label for="carne">Escolha a carne do seu burger:</label>
        <select id="carne" name="carne" v-model="carne">
          <option value="">Selecione o tipo de carne</option>
          <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
        </select>
      </div>
      <div class="input-container" id="opcionais-container">
        <label for="opcionais" id="opcionais-title">Selecione os opcionais:</label>
        <div class="checkbox-container" v-for="opcional in opcionaisData" :key="opcional.id">
          <input type="checkbox" name="opcionais[]" :id="opcional.tipo" v-model="opcionais" :value="opcional.tipo" />
          <label :for="opcional.tipo">{{ opcional.tipo }}</label>
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
    name: 'BurgerForm',
    data() {
      return {
        paes: null,
        carnes: null,
        opcionaisData: null,
        nome: null,
        pao: null,
        carne: null,
        opcionais: [],
        msg: null
      }
    },
    methods: {
      async getIngredientes() {
        const response = await fetch('http://localhost:3000/ingredientes')
        const data = await response.json()

        this.paes = data.paes
        this.carnes = data.carnes
        this.opcionaisData = data.opcionais
      },
      async createBurger(e) {
        e.preventDefault();

        const data = {
          nome: this.nome,
          pao: this.pao,
          carne: this.carne,
          opcionais: Array.from(this.opcionais),
          status: 'Solicitado'
        }

        const response = await fetch('http://localhost:3000/burgers', {
          method: 'POST',
          body: JSON.stringify(data),
          headers: {
            'Content-Type': 'application/json'
          }
        })

        this.nome = null
        this.carne = null
        this.pao = null
        this.opcionais = []
      }
    },
    mounted() {
      this.getIngredientes()
    }
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
