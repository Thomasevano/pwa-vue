<template>
  <div class="list">
    <h1>Tous les articles</h1>
    <ul>
      <li v-for="post in posts" :key="post.id">
        <article class="media">
          <figure>
            <img
              v-if="post.image"
              :src="post.image"
              alt=""
            >
            <img
              v-else
              src="http://via.placeholder.com/250x250"
              alt=""
            >
          </figure>
          <h2>{{ post.title }}</h2>
          <p>{{ post.description }}</p>
        </article>
        <div class="button">
          <router-link :to="'/article/' + post.id">Lire l'article</router-link>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'List',
  created() {
    fetch('https://jsonplaceholder.typicode.com/posts').then((response) => {
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

ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
  display: flex;
  width: 50%;
  border: black 1px solid;
}
li img {
  width: 50%;
}
.button {
  width: 156px;
  height: 40px;
  background: black;
}
.button a {
  font-size: 14px;
  line-height: 40px;
  color: white;
  text-decoration: none;
}

</style>
