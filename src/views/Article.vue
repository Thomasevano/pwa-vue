<template>
  <div v-if="post" class="post">
    <h1 class="article_title">{{ post.title }}</h1>

    <img v-if="post.img" :src="post.img" alt="article image">
    <img v-else src="http://via.placeholder.com/250x250" alt="article image">

    <div class="article_details">
      <span class="article_author">{{ post.author }}</span>
      <span class="article_date">{{ post.date }}</span>
    </div>
    
    <p class="article_content intro">{{ post.description }}</p>
    <p class="article_content">{{ post.body }}</p>
    <p class="article_content">{{ post.body }}</p>

    <a href="#" class="buy_button">Acheter</a>

    <ul class="article_img">
      <li>
        <img v-if="post.img2" :src="post.img2" alt="article image">
        <img v-else src="http://via.placeholder.com/250x250" alt="article image">
      </li>
      <li>
        <img v-if="post.img3" :src="post.img3" alt="article image">
        <img v-else src="http://via.placeholder.com/250x250" alt="article image">
      </li>
      <li>
        <img v-if="post.img4" :src="post.img4" alt="article image">
        <img v-else src="http://via.placeholder.com/250x250" alt="article image">
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Article',
  created() {
    fetch(`https://tp-vuepwa.glitch.me/${ this.$route.params.slug }`).then((response) => {
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

<style scoped>

* {
  font-family: 'Futura book';
}
li {
  list-style: none;
}

.post {
  width: 375px;
}

.article_title {
  font-size: 22px;
  font-weight: bold;
  text-align: center;
  text-transform: uppercase;
  margin: 20px auto;
}

img {
  width: 100%;
  height: 297px;
  margin-bottom: 20px;
  object-fit: cover;
}

/* .article_img {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
} */
.article_img {
  padding-left: 0;
}
.article_img li{
  width: 100%;
}

.article_details {
  display: inline-block;
  width: 100%;
  font-weight: bold;
  margin-bottom: 20px;
}
.article_author, .article_date {
  text-decoration: underline;
}
.article_details .article_author {
  float: left;
  margin-left: 30px;
}
.article_details .article_date {
  float: right;
  margin-right: 30px;
}
.article_content {
  width: 335px;
  margin: 0 auto 20px;
  font-size: 14px;
  text-align: left;
}
.intro {
  font-weight: bold;
}
.buy_button {
  display: inline-block;
  background-color: black;
  color: white;
  border: 2px solid transparent;
  cursor: pointer;
  font-size: 14px;
  font-weight: 500;
  transition: all 0.2s ease;
  padding: 10px 55px;
  text-decoration: none;
  margin: 20px 0 40px;
}
.buy_button:hover {
  background-color: white;
  color: black;
  border-color: black;
}

@media (min-width: 600px) {
  .post {
    width: 1000px;
    margin: 0 auto;
  }
  .article_img {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-between;
  }
  .article_img li{
    width: calc(100%/2 - 5px);
  }
  .article_img li:nth-last-child(1) {
    width: 100%;
  }
  img {
    width: 100%;
    height: 500px;
  }
  .article_title {
    font-size: 42px;
    margin: 60px auto 40px;
  }
  .article_content {
    font-size: 18px;
    width: 950px;
  }
}
</style>