<template>
  <div class="app">
    <header>
      <strong>Vue Nutri</strong>
    </header>

    <article v-for="(item, index) in nutri" :key="index">
      <strong>{{ item.titulo }}</strong>
      <img :src="item.capa" />
      <span>Categoria: {{ item.categoria }}</span>
      <p>{{ item.subtitulo }}</p>
    </article>
  </div>
</template>

<script>
import api from "./services/api";

export default {
  name: "App",
  data() {
    return {
      nutri: [],
    };
  },
  async created() {
    const response = await api.get("?api=posts");
    const data = await response.data;

    this.nutri = data;
    console.log(data);
  },
};
</script>

<style></style>
