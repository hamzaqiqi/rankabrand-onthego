<template>
    <div>
      <page-header>
        <input type="search"
          :value="query"
          @input="e => onQuery(e.target.value)"
          @keypress="e => onQuery(e.target.value)"
          ref="query"
          placeholder="Winkel of merknaam"
          autocomplete="off" />
      </page-header>

      <ul class="results">  
        <li v-if="query && results.length === 0">
          <span>Geen resultaten</span>
        </li>
        <li v-else
          v-for="(result, index) in results"
          :key="index"
          class="search-result">
            <router-link :to="`/ranking/${result._id}`" v-html="highlight(result.name, query)"></router-link>
        </li>
      </ul>  
    </div>
</template>

<script>
import { request } from 'graphql-request'
import config from '../../config/client'
import PageHeader from './PageHeader.vue'

const delay = (function () {
  let timer = 0
  return (callback, ms) => {
    clearTimeout(timer)
    timer = setTimeout(callback, ms)
  }
})()

export default {
  name: 'search',
  components: {
    PageHeader
  },
  data () {
    return {
      query: '',
      results: []
    }
  },
  mounted () {
    this.$refs.query.focus()
  },
  methods: {
    async onQuery (query) {
      query = query.trim()
      this.query = query

      delay(async () => {
        // No query anymore? Clear result list
        if (!query || query === '') {
          this.results = []
          return
        }

        this.results = (await request(`${config.api.url}/graphql`,
          `{
              getRankingsByQuery(query: "${query}") {
                _id
                name
              }
          }`)).getRankingsByQuery
      }, 100)
    },
    highlight (text, highlight) {
      const t = text.replace(new RegExp(highlight, 'i'), `<span>$&</span>`)
      return t
    }
  }
}
</script>

<style scoped>

.header input {
  border: 0;
  border-bottom: 1.5px solid #000;
  margin-left: 20px;
  margin-top: 6px;
  padding: 13px 15px 3px 25px;
  height: 38px;
  font-size: 17px;
  line-height: 15px;
  width: calc(100% - 90px);
  background-image: url(/static/img/search.svg);
  background-repeat: no-repeat;
  background-position: 0px 14px;
  font-weight: bold;
  background-size: 21px;
}

.results {
  display: flex;
  flex-flow: column;
  overflow: auto;
  margin: 0;
  padding: 0;
  list-style: none;
}

.results li {
  border-bottom: 1px solid lightgrey;
}

a, span {
  display: block;
  background: white;
  text-align: left;
  padding: 1em;
  text-decoration: none;
  color: grey;
  font-weight: 700;
}
a {
    cursor: pointer;
}

</style>

<style>
li.search-result a span {
    color: black;
}
</style>
