<template>
  <header>
    <router-link to="/">
      <h1><span>Vue</span>Movies</h1>
    </router-link>
  </header>
  <main>
    <router-view />
  </main>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;

  &::selection {
    background-color: transparentize(#42b883, 0.5);
  }
}

body {
  background-color: #35495e;
  min-height: 100vh;

  main {
    margin: 0 auto;
    max-width: 700px;
  }
}

a {
  text-decoration: none;
}

header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px 16px;
  background-color: #2c3d4e;
  box-shadow: 0 0 6px rgba(0, 0, 0, 0.1);

  h1 {
    color: #fff;
    font-size: 28px;

    span {
      color: #42b883;
    }
  }
}
</style>
