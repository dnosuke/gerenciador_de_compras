<template>
  <div id="Body">
    <form v-on:submit.prevent="addProduto">
      <label for="new-produto"><h1>adicione sua compras:</h1></label>
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
        <option>10 itens ou Mais</option>
        </select>
      <button>adicionar</button>
      <hr>

      <div :class="bloco_compra" v-for="produto in compras" :key="produto">
        <input type="checkbox">
          <big>
            {{produto.id}}
            {{produto.title}}
            {{produto.loja}}
            {{produto.preco}}
            {{produto.quant}}
          </big>
          <span>
            <button @click="removeProduto(produto)">x</button>
          </span>
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
        newQuant: '',
        compras: []
      }
    },
    methods: {
      addProduto: function () {
        this.compras.push({
          id: this.idCompra++,
          title: this.newProduto,
          loja: this.newLoja,
          preco: this.newPreco,
          quant: this.newQuant
        })
        this.newProduto = ''
        this.newLoja = ''
        this.newPreco = ''
        this.newQuant = ''
      },
      removeProduto: function(produto) {
        this.compras.splice(this.compras.indexOf(produto), 1)
      }
    }
  }
</script>

<style>
.bloco_compra {
  position: relative;
  box-sizing: border-box;
  width: 350px;
  height: 150px;
  padding: 10px;
  border-radius: 8px;
  font-size: 2rem;
  font-weight: 300;
  cursor: pointer;
  user-select: none;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #DDD;
  border-left: 12px solid #0A8F08;
  background-color: #4CAF50;
  text-decoration: line-through;
}
</style>