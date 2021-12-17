<template>
  <div class="movie-detail">
    <h2>Movie: {{ movie.Title }}</h2>
    <p class="type">{{ movie.Type }}</p>
    <div class="poster">
      <img :src="movie.Poster" alt="Movie Poster" class="featured-img" />
      <div class="poster-detail">
        <p><span class="headings">Name:</span> {{ movie.Title }}</p>
        <p><span class="headings">Director:</span> {{ movie.Director }}</p>
        <p><span class="headings">Actors:</span> {{ movie.Actors }}</p>
        <p><span class="headings">Genre:</span> {{ movie.Genre }}</p>
        <p><span class="headings">Released:</span> {{ movie.Released }}</p>
        <p><span class="headings">Votes:</span> {{ movie.imdbVotes }}</p>
        <p>
          <span class="headings">Rating: </span>
          <span class="rating">{{ movie.imdbRating }}</span>
        </p>
      </div>
    </div>
    <h3>Description</h3>
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

  h3 {
    color: #fff;
    font-size: 24px;
    margin-top: 16px;
    margin-bottom: 16px;
  }

  .poster {
    display: flex;
    margin-top: 20px;
    margin-bottom: 20px;

    &-detail {
      display: flex;
      flex-direction: column;
      justify-content: space-around;

      .headings {
        font-weight: bold;
        color: #42b883;
      }

      .rating {
        background-color: #ecbd0f;
        padding: 6px;
        border-radius: 4px;
      }
    }

    .featured-img {
      max-width: 200px;
    }

    p {
      margin-left: 40px;
      font-size: 18px;
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
    border-radius: 8px;
  }
}
</style>
