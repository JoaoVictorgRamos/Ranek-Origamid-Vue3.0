<template>
  <section class="produtos-container">
    <div v-for="produto in produtos" :key="produto.id">
      <img
        v-if="produto.fotos"
        :src="produto.fotos[0].src"
        :alt="produto.fotos[0].titulo"
      />
      <h2 class="titulo">{{ produto.nome }}</h2>
      <p class="preco">{{ produto.preco }}</p>
      <p>{{ produto.descricao }}</p>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      produtos: null,
    };
  },
  methods: {
    getProdutos() {
      fetch("http://localhost:3000/produto")
        .then((r) => r.json())
        .then((r) => (this.produtos = r));
    },
  },
  created() {
    this.getProdutos();
  },
};
</script>

<style></style>