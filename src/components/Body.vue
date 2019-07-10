<template>
  <div id="Body">
    <form v-on:submit.prevent="addProduto">
      <label for="new-produto"><h1>adicione sua comprar:</h1></label>
      <p>o produto comprado:<input v-model="newProduto" id="new-produto" placeholder="Ex.: camisa"></p>
      <p>a loja visitada:<input v-model="newLoja" id="new-produto" placeholder="Ex.: Riachuelo"></p>
      <p>o preço da compra:<input v-model="newPreco" id="new-produto" placeholder="Ex.: R$ 29.99"></p>
      <select v-model="newQuant" id="new-produto">
        <option disabled value="">Escolha um item</option>
        <option>1</option>
        <option>2</option>
        <option>3</option>
        <option>4</option>
        <option>5</option>
        <option>6</option>
        <option>7</option>
        <option>8</option>
        <option>9</option>
        <option>1O itens ou Mais</option>
        </select>
      <button>adicionar</button>
      <hr>

      <div id="lista">
        <appLista/>
      </div>

    </form>
  </div>
</template>

<script>
  import appLista from './Lista.vue';

  export default {
    components: {appLista},
    name: 'Body',
    data(){
      return {
        idCompra: 1,
        newProduto: '',
        newLoja: '',
        newPreco: '',
        newQuant: '',
        compras: []
      }
    },
    methods: {
      addProduto: function () {
        this.compras.push({
          id: this.idCompra++,
          title: this.newProduto,
          produto: this.newLoja,
          preco: this.newPreco,
          quant: this.newQuant
        })
        this.newProduto = ''
        this.newLoja = ''
        this.newPreco = ''
        this.newQuant = ''
      }
    }
  }
</script>

<style>
#Body {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>