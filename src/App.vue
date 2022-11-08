<template>
  <div class="app">
    <header>
      <div class="container">
        <button>Dark Mode</button>
        <strong>Vue Nutri</strong>
      </div>
    </header>

    <main>
      <div class="loading" v-if="loading">
        <h2>Carregando...</h2>
      </div>
      <div else>
        <article v-for="(item, index) in nutri" :key="index">
          <strong>{{ item.titulo }}</strong>
          <img :src="item.capa" />
          <span>Categoria: {{ item.categoria }}</span>
          <p>{{ item.subtitulo }}</p>
        </article>
      </div>
    </main>
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
  height: 10vh;
}

header .container {
  width: 80%;
  height: 100%;

  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 0 auto;
}

main {
  margin-top: 4rem;
}
</style>
