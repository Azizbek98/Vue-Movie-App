<template>
  <header>
    <router-link to="/">
      <h1><span>Vue</span> Movies</h1>
    </router-link>
  </header>
  <main>
    <router-view />
  </main>
  <footer>
    <p>Footer</p>
  </footer>
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
</style>
