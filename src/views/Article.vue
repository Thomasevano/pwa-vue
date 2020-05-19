<template>
  <div v-if="post">
    <img  
      v-if="article1_img"
      :src="article1_img"
      alt=""
    >
    <img
      v-else
      src="http://via.placeholder.com/250x250"
      alt=""
    >
    <h1>{{ post.title }}</h1>
    <p>{{ post.body }}</p>
  </div>
</template>

<script>
export default {
  name: 'Article',
  created() {
    fetch(`https://jsonplaceholder.typicode.com/posts/${ this.$route.params.slug }`).then((response) => {
      response.json().then((data) => {
        this.post = data
      })
    })
  },
  data() {
    return {
      post: [],
    }
  }
}
</script>