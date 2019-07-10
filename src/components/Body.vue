<template>
  <div id="Body">
    <form v-on:submit.prevent="addProduto">
      <label for="new-produto"><h1>adicione sua comprar:</h1></label>
      <p>o produto comprado:<input v-model="newProduto" id="new-produto" placeholder="Ex.: camisa"></p>
      <p>a loja visitada:<input v-model="newLoja" id="new-produto" placeholder="Ex.: Riachuelo"></p>
      <p>o preço da compra:<input v-model="newPreco" id="new-produto" placeholder="Ex.: R$ 29.99"></p>
      <button>adicionar</button>
      <hr>
      <div id="lista">
        {{produtos}}
        <br>
      </div>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'Body',
    data(){
      return {
        idCompra: 1,
        newProduto: '',
        newLoja: '',
        newPreco: '',
        produtos: []
      }
    },
    methods: {
      addProduto: function () {
        this.produtos.push({
          id: this.idCompra++,
          title: this.newProduto,
          produto: this.newLoja,
          preco: this.newPreco
        })
        this.newProduto = ''
        this.newLoja = ''
        this.newPreco = ''
      },
      removeCompra(livro){
        this.livros.splice(this.livros.indexOf(livro), 1)
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