<template>
  <h1>{{ mensaje }}</h1>
</template>
<script>
import axios from "axios";
import env from "../config/env";
export default {
  name: "IndexPage",
  data() {
    return {
      mensaje: ""
    };
  },
  created() {
    axios.get(`${env.endpoint}/albums`).then(response => {
      this.mensaje = response.status;
    });
  }
};
</script>

<style scoped>
</style>