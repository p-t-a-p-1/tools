<template>
  <div class="movie">
    <div class="nes-field search-box">
        <input type="text" id="name_field" class="nes-input search-box__input" v-model="searchStr" placeholder="enter movie title" />
        <button type="button" class="nes-btn search-box__btn" @click="onClick">Search</button>
    </div>
    <pre>{{ results }}</pre>

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
</style>

<script>
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
      })
    }
  }
}


</script>
