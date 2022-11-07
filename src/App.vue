<template>
  <div class="app">
    <header>
      <strong>Vue Nutri</strong>
    </header>

    <div class="loading" v-if="loading">
      <h2>Carregando</h2>
    </div>
    <div else>
      <article v-for="(item, index) in nutri" :key="index">
        <strong>{{ item.titulo }}</strong>
        <img :src="item.capa" />
        <span>Categoria: {{ item.categoria }}</span>
        <p>{{ item.subtitulo }}</p>
      </article>
    </div>
  </div>
</template>

<script>
import api from "./services/api";

export default {
  name: "App",
  data() {
    return {
      nutri: [],
      loading: true,
    };
  },
  async created() {
    const response = await api.get("?api=posts");
    const data = await response.data;

    this.nutri = data;
    this.loading = false;
  },
};
</script>

<style scoped>
header {
  background: red;
}
</style>
