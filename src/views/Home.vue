<template>
  <div class="home">
      <div v-for="post in latestPosts" :key="post.id" class="lastest-articles">
        <router-link :to="'/article/' + post.id">
          <figure>
            <img v-if="post.img" :src="post.img" alt="article image">
            <img v-else src="http://via.placeholder.com/250x250" alt="article image">
          </figure>
          <span>{{ post.author }}</span>
          <span>{{ post.date }}</span>
          <h2>{{ post.title }}</h2>
          <p>{{ post.description}}</p>
        </router-link>
      </div>
    </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  computed: {
    latestPosts: function () {
      return this.posts.filter(function (post) {
        return post.id < 5 & post.id > 1
      })
    }
  },
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
