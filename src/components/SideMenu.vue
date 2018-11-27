<template>
  <div id="menu">
    <div class="menu-button">
        <div />
        <div />
        <div />
    </div>
    <div class="sidebar">
    </div>
  </div>
</template>

<script>

export default {
  name: 'sidemenu'
}
</script>

<style scoped>
.menu-button {
    width: 35px;
    position: fixed;
    cursor: pointer;
    right: 16px;
    top: 8px;
    z-index: 2;
}
.menu-button > div {
    height: 4px;
    width: 100%;
    margin: 8px 0;
    background-color: #000;
}
.sidebar {
    display: none;
}
</style>
