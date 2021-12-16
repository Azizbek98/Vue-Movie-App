<template>
  <div class="movie-detail">
    <h2>Movie title {{ $route.params.id }}</h2>
  </div>
</template>

<script>
import { ref, onBeforeMount } from "vue";
import { useRoute } from "vue-router";
import env from "@/env.js";

export default {
  setup() {
    const movie = ref({});
    const route = useRoute();

    onBeforeMount(() => {
      fetch(
        `http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`
      )
        .then((response) => response.json())
        .then((data) => {});
    });

    return {
      movie,
    };
  },
};

// Detail {{ $route.params.id }}
</script>

<style></style>
