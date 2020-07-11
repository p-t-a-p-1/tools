<template>
  <div class="movie">
    <div class="nes-field search-box">
        <input type="text" id="name_field" class="nes-input search-box__input" v-model="searchStr" placeholder="enter movie title" />
        <button type="button" class="nes-btn search-box__btn" @click="onClick">Search</button>
    </div>

    <magic-grid class="posts-list">
      <div class="posts-item nes-container with-title is-centered" v-for="(post, index) in results" :key="index">
        <p class="title">{{post.Title}}</p>
        <p>{{post.Year}}</p>
        <img :src="post.Poster" :alt="post.Title">
      </div>
    </magic-grid>
  </div>
</template>

<style lang="scss">
.search-box {
  display: flex;
  &__input {
    width: 80%;
  }
  &__btn {
    width: 20%;
  }
}
.posts-list {
  margin-top: 2.5rem;
}
.posts-item {
  img {
    width: 100%;
  }
}
</style>

<script>
import MagicGrid from 'vue-magic-grid'
import Vue from 'vue'

let baseUrl = process.env.VUE_APP_MOVIE_API_URL
export default {
  name: 'movie',
  data () {
    return {
      searchStr: '',
      results: []
    }
  },
  methods: {
    onClick: function() {
      if (this.searchStr === '') {
          return
      }
      baseUrl = baseUrl + '&s=' + this.searchStr
      this.axios.get(baseUrl)
      .then(response => {
          this.results = response.data.Search
          Vue.use(MagicGrid)
      })
    }
  }
}
</script>
