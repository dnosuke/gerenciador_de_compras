<template>
    <div id="lista">
        <ul>
            <li
            is="produto-item"
            v-for="(produto, index) in compras"
            v-bind:key="produto.id"
            v-bind:title="produto.title"
            v-bind:produto="produto.produto"
            v-bind:preco='produto.preco'
            v-bind:quant='produto.quant'
            v-on:remove="compras.splice(index, 1)"
            ></li>
        </ul>
    </div>
</template>

<script>
export default {
    props: ['newProduto','newLoja','newPreco','newQuant'],

}
</script>

<style>

</style>
