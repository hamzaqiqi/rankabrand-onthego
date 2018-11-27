<template>
  <div class="header">
    <div class="space" />
    <div class="bar">
      <div>
        <router-link to="/" class="back-button">
          <img src="/static/img/arrow.svg" />
        </router-link>
      </div>
      <div>
        <slot />
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.header .space {
  width: 100%;  
  height: 60px;
}
.header .bar {
  width: 100%;
  height: 60px;
  position: fixed;
  top: 0;
  box-shadow: 0 2px 2px 1px rgba(0,0,0,0.06);
  background-color: #fff;
  z-index: 1;
  border-bottom: 1px solid lightgrey;
  display: flex;

  div:nth-child(1) {
    flex: 1;
    flex-grow: 0;
  }
  div:nth-child(2) {
    flex: 1;
    flex-grow: 1;
  }

  .back-button {
    display: inline-block;
    margin: 15px;
  }
  .back-button img {
    width: 30px;
    height: 30px;
  }
}
</style>