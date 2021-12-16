<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt1375666">
        <img src="#" alt="movie-image" class="featured-img" />
        <div class="details">
          <h3>Inception</h3>
          <p>Description here:</p>
        </div>
      </router-link>
    </div>

    <form @submit.prevent="" class="search-box">
      <input type="text" placeholder="What are you looking for ?" />
      <input type="submit" value="Search" />
    </form>

    <div class="movies-list">MOVIES</div>
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

    .featured-img {
      display: block;
      widows: 100%;
      height: 300px;
      object-fit: cover;

      position: relative;
      z-index: 0;
    }

    .details {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba($color: #000000, $alpha: 0.5);
      padding: 16px;
      z-index: 1;

      h3 {
        color: #fff;
        margin-bottom: 16px;
      }

      p {
        color: #fff;
      }
    }
  }

  .search-box {
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    padding: 16px;

    input {
      display: block;
      appearance: none;
      border: none;
      outline: none;
      background: none;

      &[type="text"] {
        width: 100%;
        color: #fff;
        background-color: #496583;
        font-size: 20px;
        padding: 10px 16px;
        border-radius: 8px;
        margin-bottom: 15px;
        transition: 0.4s;

        &::placeholder {
          color: #f3f3f3;
        }

        &:focus {
          box-shadow: 0 3px 6px rgba($color: #000000, $alpha: 0.2);
        }
      }

      &[type="submit"] {
        width: 100%;
        max-width: 300px;
        background-color: #42b883;
        padding: 16px;
        border-radius: 8px;
        color: #fff;
        font-size: 20px;
        text-transform: uppercase;
        transition: 0.4s;

        &:hover {
          cursor: pointer;
        }

        &:active {
          background-color: #3b8070;
        }
      }
    }
  }
}
</style>
