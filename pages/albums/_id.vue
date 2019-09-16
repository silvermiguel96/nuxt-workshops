<template>
  <div class="container">
    <a href="#">Regresar</a>
    <h1 class="title">{{album.title}}</h1>
    <div class="columns is-multiline">
      <div class="column is-one-quarter" v-for="photo in photos" :key="photo.id">
        <img :src="photo.url" :alt="photo.title" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import router from "vue-router";
import env from "../../config/env";

export default {
  name: "AlbumIndvPage",
  data() {
    return {
      album: {},
      photos: []
    };
  },
  created() {
    axios
      .get(`${env.endpoint}/albums/${this.$route.params.id}`)
      .then(albumResponse => {
        this.album = albumResponse.data;
      });
    axios
      .get(`${env.endpoint}/albums/${this.$route.params.id}/photos`)
      .then(photosResponse => {
        this.photos = photosResponse.data;
      });
  }
};
</script>

<style scoped>
.container {
  text-align: center;
}
.title {
  margin-top: 100px;
}
</style>