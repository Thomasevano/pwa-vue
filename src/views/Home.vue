<template>
  <div class="home">
    <h2>Welcome</h2>
    <div class="first-article">
      <figure class="first-article-img">
        <img
          v-if="posts[0].img"
          :src="posts[0].img"
          alt=""
        >
        <img
          v-else
          src="http://via.placeholder.com/250x250"
          alt=""
        >
      </figure>
      <div class="first-article-textblock">
        <div class="first-article-infos">
          <p>{{ posts[0].author }}</p>
          <p>{{ posts[0].date }}</p>
        </div>
        <h2>{{ posts[0].title }}</h2>
        <p>{{ posts[0].description}}</p>
        <div class="button">
          <router-link :to="'/article/' + posts[0]">Lire l'article</router-link>
        </div>
      </div>
    </div>

    <h2>Derniers articles</h2>
    
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
