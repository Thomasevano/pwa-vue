<template>
  <div class="home">
    <div v-for="post in posts" :key="post.id" class="last-article">
      <figure>
        <img
          src="http://via.placeholder.com/250x250"
          alt=""
        >
      </figure>
      <span>Jean claude</span>
      <span>Le 14/04/2020</span>
      <h2>{{ post.title }}</h2>
      <p>{{ post.description}}</p>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  created() {
    fetch('https://tp-vuepwa.glitch.me/').then((response) => {
      response.json().then((data) => {
        this.posts = data
      })
    })
  },
  data() {
    return {
      posts: []
    }
  }
}
</script>

<style scoped>

</style>
