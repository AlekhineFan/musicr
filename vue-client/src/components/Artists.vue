<template>
  <div>
    <h1>Artists</h1>
    <div v-for="artist in artists" :key="artist.id">
      <router-link :to="{ name: 'Artist', params: { id: artist.id } }">{{
        artist.name
      }}</router-link>
    </div>
  </div>
</template>

<script>
import { onMounted, ref } from "vue";
import request from "../../services/requests.js";

export default {
  setup() {
    let artists = ref([]);

    onMounted(() => {
      request.findAll().then((res) => {
        artists.value = res.data;
      });
    });

    return { artists };
  },
};
</script>

<style></style>
