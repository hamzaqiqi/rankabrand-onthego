<template>
    <div>
      <img class="logo" src="/static/img/logo.svg" />
      <input type="search"
        value=""
        @focus="goToSearch"
        placeholder="Winkel of merknaam"
        autocomplete="off" />
    </div>
</template>

<script>
export default {
  name: 'home',
  components: {
  },
  methods: {
    goToSearch () {
      console.log(this.$router)
      this.$router.push('/search')
    }
  }
}
</script>

<style scoped>

.logo {
  width: 304px;
  height: 110px;
  margin: 0 auto;
  display: block;
  margin-top: 125px;
}

input {
  width: 90%;
  line-height: 50px;
  padding: 5px 20px 5px 50px;
  border: 0;
  display: block;
  margin: 0 auto;
  margin-top: 100px;
  font-size: 18px;
  background-image: url('/static/img/search-grey.svg');
  background-repeat: no-repeat;
  background-position: 16px 16px;
}

</style>
