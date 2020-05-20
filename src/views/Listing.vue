<template>
  <main class="list">
    <h2 class="section-title">Tous les articles</h2>

    <section class="articles">
      <div v-for="post in posts" :key="post.id" class="article">
        <router-link :to="'/article/' + post.id">
          <div class="gradient-overlay"></div>
          <figure class="article-img">
            <img v-if="post.img" :src="post.img" alt="article image">
            <img v-else src="http://via.placeholder.com/250x250" alt="article image">
          </figure>
          <div class="article-textblock">
            <div class="article-intro">
              <p class="article-info">{{ post.author }}</p>
              <p class="article-info">{{ post.date }}</p>
              <h3 class="article-title">{{ post.title }}</h3>
            </div>
            <div class="article-description">
              <p class="description-text">{{ post.description}}</p>
              <div class="button">
                <p>Lire l'article</p>
              </div>
            </div>
          </div>
        </router-link>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: 'List',
  created() {
    fetch('https://tp-vuepwa.glitch.me/').then((response) => {
      response.json().then((data) => {
        this.posts = data
        console.log(data);
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

  * {
    margin: 0;
    padding: 0;
    font-family: 'Futura book';
  }

  .list {
    display: flex;
    flex-direction: column;
    max-width: 1100px;
    margin: 40px auto;
  }

  .button {
    display: inline-block;
    background: #000000;
    border: 3px solid #000000;
    padding: 10px 20px;
    font-size: 1rem;
    font-weight: bold;
    text-decoration: none;
    color: white;
    transition: all .2s ease;
  }

  .button:hover {
    cursor: pointer;
    background: #FFFFFF;
    border: 3px solid #000000;
    color: #000000;
  }

  .section-title {
    font-weight: bold;
    font-size: 2rem;
    text-transform: uppercase;
    margin-bottom: 40px;
  }

  .articles {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-between;
    margin-bottom: 40px;
  }

  .article {
    position: relative;
    width: 100vw;
  }

  .gradient-overlay {
    height: 100%;
    width: 100%;
    background: linear-gradient(0deg, rgba(0, 0, 0, 0.6) 0%, rgba(0, 0, 0, 0.2) 100%);
    opacity: 0.6;
    position: absolute;
    transition: all .2s ease;
  }

  .article:hover .gradient-overlay {
    opacity: 1;
  }

  .article-img {
    height: 250px;
    overflow: hidden;
    display: flex;
  }

  .article-img img {
    min-width: 100%;
    object-fit:cover;
  }

  .article-textblock {
    max-width: 350px;
    position: absolute;
    left: 10px;
    bottom: 10px;
    text-align: left;
    color: white;
  }

  .article-intro {
    margin-bottom: 10px;
    transform: translateY(175%);
    transition: all .2s ease;
  }

  .article:hover .article-intro {
    transform: translateY(0);
  }

  .article-description {
    opacity: 0;
    transition: all .2s ease;
  }

  .article:hover .article-description {
    opacity: 1;
  }

  .article-info {
    font-size: 0.8rem;
    margin-bottom: 5px;
  }

  .article-title {
    font-size: 1.2rem;
    font-weight: bold;
    text-transform: uppercase;
  }

  .description-text {
    font-size: 1rem;
    margin-bottom: 5px;
  }

  .article .button {
    background: #FFFFFF;
    color: #000000;
  }

  @media (min-width: 600px) { 
    .article {
      position: relative;
      width: calc(100%/2 - 5px);
      margin-bottom: 10px;
    }
  }

</style>