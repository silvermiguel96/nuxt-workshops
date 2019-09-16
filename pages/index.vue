<template>
  <div class="">
    <h1>Albums de la pagina</h1>
    <div v-for="album in albums" :key="album.title">
      <p>{{ album.title }}</p>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import env from "../config/env";
export default {
  name: "IndexPage",
  data() {
    return {
      albums: []
    };
  },
  created() {
    axios.get(`${env.endpoint}/albums`).then(response => {
      this.albums = response.data;
    });
  }
};
</script>

<style scoped>
</style>