<template>
  <div id="app">
    <main>
      <router-view></router-view>
      <side-menu />
    </main>
  </div>
</template>

<script>
import SideMenu from './components/SideMenu.vue'

export default {
  name: 'app',
  components: {
    SideMenu
  }
}
</script>

<style lang="scss">
@import './assets/scss/variables.scss';

body {
  margin: 0;
  background-color: #f3f3f3;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

main {
  position: relative;
  overflow: auto;
}

a {
  color: $primary;
}
a:visited {
  color: $primary;
}

p {
  margin: 0 0 15px 0;
}

::-webkit-input-placeholder {
  font-style: italic;
  color: #a5a5a5;
  opacity: 1;
  font-weight: normal;
}
:-moz-placeholder {
  font-style: italic;
  color: #a5a5a5;
  opacity: 1;
  font-weight: normal;
}
::-moz-placeholder {
  font-style: italic;
  color: #a5a5a5;
  opacity: 1;
  font-weight: normal;
}
:-ms-input-placeholder {
  font-style: italic;
  color: #a5a5a5;
  opacity: 1;
  font-weight: normal;
}

input:focus,
select:focus,
textarea:focus,
button:focus {
  outline: none;
}
</style>
