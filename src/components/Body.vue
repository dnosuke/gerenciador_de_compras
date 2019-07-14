<template>
  <div id="Body">
    <div class="caixa">
      <h1>Adicione suas compras:</h1>
      <form v-on:submit.prevent="addProduto">
        <label for="new-produto"></label>
        <span>
          <table>
            <tr>
              <th class="tabtext"><span>O produto comprado:</span></th>
              <th class="tabinp"><input class="form-control" v-model="newProduto" id="new-produto" placeholder="Ex.: camisa" maxlength="20"></th>
            </tr>
            <tr>
              <th class="tabtext"><span>A loja visitada:</span></th>
              <th class="tabinp"><input class="form-control" v-model="newLoja" id="new-produto" placeholder="Ex.: Riachuelo" maxlength="20"></th>
            </tr>
            <tr>
              <th class="tabtext"><span>O preço da compra:</span></th>
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
              <th class="tabtext"><span>Quantidade:</span></th>
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
                <option>10</option>
              </select>
              </th>
            </tr>
          </table>
        </span>
        <div class="btn">
          <button class="btn btn-dark" @click="calcularGastos">Adicionar</button><br>
        </div>
      </form>
      
    </div>
    
    <div>
      <table class="lista" align="center">
        <tr class="contlist">
          <th colspan="5">Lista de compras realizadas :{{valorTotal}}</th>
        </tr>
        <tr class="contlist">
          <th>Produto</th>
          <th>Loja</th>
          <th>Preço</th>
          <th>Quantidade</th>
        </tr>
        <tr class="contlist" v-for="produto in compras" :key="produto.id">
          <th>{{produto.title}}</th>
          <th>{{produto.loja}}</th>
          <th>{{produto.preco}}</th>
          <th>{{produto.quant}}</th>
        </tr>
          <button class="btn btn-outline-danger" @click="removeProduto(produto)">x</button>
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
        valorTotal: 0,
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
          quant: this.newQuant,
          total: this.newPreco * this.newQuant
        })
        this.newProduto = ''
        this.newLoja = ''
        this.newPreco = null
        this.newQuant = 1
      },
      removeProduto: function(produto) {
        this.compras.splice(this.compras.indexOf(produto), 1)
      },
      calcularGastos(){
        this.valorTotal = this.newPreco * this.newQuant + this.valorTotal
      }
    }
  }
</script>

<style>
.caixa {
  background-color: #34A8DB;

  margin-top: 0px;
  margin-bottom: 30px;
  margin-right: 0px;
  margin-left: 410px;

  padding-top: 0px;
  padding-right: 0px;
  padding-left: 20px;
  padding-bottom: 10px;

  height: auto;
  width: 450px;
  position: relative;
  box-shadow:0 4px 8px 0 rgba(0, 0, 0, 0.479), 0 6px 20px 0 rgb(0, 0, 0);
}
.lista {
  border-collapse: collapse;
  width: 50%;
}
.contlist > th {
  width: 10%;
  padding: 8px;
  text-align: center;
  border-bottom: 2px solid black;
}
.contlist:hover {background-color:red;}
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