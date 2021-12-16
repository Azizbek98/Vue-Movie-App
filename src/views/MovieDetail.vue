<template>
  <div class="movie-detail">
    <h2>{{ movie.Title }}</h2>
    <p class="type">{{ movie.Type }}</p>
    <div class="poster">
      <img :src="movie.Poster" alt="Movie Poster" class="featured-img" />
      <p>{{ movie.Released }}</p>
    </div>
    <p>{{ movie.Plot }}</p>
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
        .then((data) => {
          movie.value = data;
          console.log(data);
        });
    });

    return {
      movie,
    };
  },
};

// Detail {{ $route.params.id }}
</script>

<style lang="scss">
.movie-detail {
  padding: 16px;

  h2 {
    color: #fff;
    font-size: 30px;
    font-weight: 600;
    margin-bottom: 16px;
  }

  .poster {
    display: flex;
    margin-top: 16px;
    margin-bottom: 16px;

    .featured-img {
      max-width: 200px;
    }

    p {
      margin-left: 30px;
      font-size: 20px;
    }
  }

  p {
    color: #fff;
    font-size: 18px;
    line-height: 1.4;
  }

  .type {
    background-color: #42b883;
    width: 80px;
    font-size: 20px;
    text-align: center;
    font-weight: bold;
  }
}
</style>
