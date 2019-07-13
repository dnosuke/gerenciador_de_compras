<template>
  <div id="Body">
    <div class="caixa">
      <h1>adicione suas compras:</h1>
      <form v-on:submit.prevent="addProduto">
        <label for="new-produto"></label>
        <table>
          <tr>
            <th class="tabtext"><span>o produto comprado:</span></th>
            <th class="tabinp"><input class="form-control" v-model="newProduto" id="new-produto" placeholder="Ex.: camisa"></th>
          </tr>
          <tr>
            <th class="tabtext"><span>a loja visitada:</span></th>
            <th class="tabinp"><input class="form-control" v-model="newLoja" id="new-produto" placeholder="Ex.: Riachuelo"></th>
          </tr>
          <tr>
            <th class="tabtext"><span>o preço da compra:</span></th>
            <th class="tabinp"><input 
              v-model="newPreco" 
              class="form-control"
              id="new-produto" 
              type="number" 
              placeholder="Ex.: R$ 29.99" 
              min="0.0" max="100000.0">
            </th>
          </tr>
          <tr>
            <th class="tabtext"><span>quantidade:</span></th>
            <th class="tabinp">
              <select class="form-control" v-model="newQuant" id="new-produto"><br>
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
            </th>
          </tr>
        </table>
      </form>
      <div class="btn">
        <button type="button" class="btn btn-outline-dark" @click="addProduto">adicionar</button><br>
      </div>
    </div>
    

    <div>
      <table class="table">
        <tr>
          <th>lista de compras realizadas</th>
        </tr>
        <tr>
          <th>
            <section class="lista_compra" v-for="produto in compras" :key="produto.id">
              produto:{{produto.title}},
              loja:{{produto.loja}},
              preço:{{produto.preco}},
              quantidade:{{produto.quant}}
              <span>
                <button type="button" class="btn btn-outline-danger" @click="removeProduto(produto)">x</button>
              </span>
            </section>
          </th>
        </tr>
      </table>
    </div>
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
        newPreco: null,
        newQuant: 1,
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
        this.newPreco = null
        this.newQuant = 1
      },
      removeProduto: function(produto) {
        this.compras.splice(this.compras.indexOf(produto), 1)
      }
    }
  }
</script>

<style>
.caixa {
  background-color: #34A8DB;

  margin-top: 0px;
  margin-bottom: 0px;
  margin-right: 0px;
  margin-left: 410px;

  padding-top: 0px;
  padding-right: 0px;
  padding-left: 20px;
  padding-bottom: 10px;

  height: auto;
  width: 450px;
  position: relative;
}
h1 {
  color: #FFFFFF;
  text-align: justify;
}
.tabtext {
  text-align: right;
  color: #FFFFFF;
}
.tabinp {
  text-align: left;
}
</style>