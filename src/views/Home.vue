<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt1375666">
        <img src="" alt="movie-image" />
        <div class="detail">
          <h3>Inception</h3>
          <p>Description here:</p>
        </div>
      </router-link>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {};
</script>

<style lang="scss">
.home {
  .feature-card {
    position: relative;
  }
}
</style>
