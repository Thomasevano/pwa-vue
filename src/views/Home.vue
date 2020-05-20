<template>
  <main class="home">
    <section class="first-article">
      <figure class="first-article-img">
        <img v-if="posts[0].img" :src="posts[0].img" alt=""/>
        <img v-else src="http://via.placeholder.com/250x250" alt=""/>
      </figure>

      <div class="first-article-textblock">
        <div class="first-article-infos">
          <p>{{ posts[0].author }}</p>
          <p>{{ posts[0].date }}</p>
        </div>
        <h3 class="first-article-title">{{ posts[0].title }}</h3>
        <p class="first-article-description">{{ posts[0].description}}</p>

        <router-link :to="'/article/' + posts[0].id">
          <div class="button large">
            <p>Lire l'article</p>
          </div>
        </router-link>

      </div>
    </section>

    <h2 class="section-title">Derniers articles</h2>

    <section class="latest-articles">
      <div v-for="post in latestPosts" :key="post.id" class="article">
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

    <router-link to="/listing">
      <div class="button large">
        <p>Tous les articles</p>
      </div>
    </router-link>
  </main>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  computed: {
    latestPosts: function () {
      return this.posts.filter(function (post) {
        return post.id <= 5 & post.id > 1
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

  * {
    margin: 0;
    padding: 0;
    font-family: 'Futura book';
  }

  .home {
    display: flex;
    flex-direction: column;
    max-width: 1100px;
    margin: auto;
  }

  .first-article-img {
    display: flex;
    height: 300px;
  }

  .first-article-img img {
    min-width: 100%;
    object-fit: cover;
  }

  .first-article-textblock {
    position: relative; 
    top: -40px;
    left: 0; 
    right: 0; 
    margin-left: auto; 
    margin-right: auto; 
    width: 80vw;
    max-width: 500px;
    margin: 0px auto;
    
    padding: 20px;
    background: #FFFFFF;
    border: 3px solid #000000;
    border-radius: 2px;
  }

  .first-article-infos {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 20px;
  }

  .first-article-infos p {
    font-size: 0.8rem;
    font-weight: bold;
    position: relative;
  }

  .first-article-infos p::after {
    content: '';
    position: absolute;
    left: 0;
    bottom: -3px;
    height: 2px;
    width: 100%;
    background: #000000;
  }

  .first-article-title {
    font-size: 1.2rem;
    text-transform: uppercase;
    margin-bottom: 20px;
  }

  .first-article-description {
    font-size: 1rem;
    margin-bottom: 20px;
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

  .button.large {
    width: 200px;
  }

  .section-title {
    font-weight: bold;
    font-size: 2rem;
    text-transform: uppercase;
    margin-bottom: 40px;
  }

  .latest-articles {
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
    .home {
      margin: 40px auto;
    }
    
    .first-article-img {
      height: 500px;
    }

    .article {
      position: relative;
      width: calc(100%/2 - 5px);
      margin-bottom: 10px;
    }
  }

</style>