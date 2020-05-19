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
          <router-link :to="'article/' + post.id">Lire l'article</router-link>
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
        console.log(data)
      })
    })
  },
  data() {
    return {
      posts1: [],
      
      posts: [
        {
          id: 1,
          title: "Air Jordan 4 green metallic",
          date: "01 May 2017",
          description: "Jordan Brand lève le voile sur une nouvelle Air Jordan 4 Metallic Green dans le cadre du 30ème anniversaire du design de Tinker Hatfield.",
          image: "https://www.lesitedelasneaker.com/wp-content/images/2020/04/air-jordan-4-green-metallic-ct8527-113-pic1-1100x733.jpg"
        },
        {
          id: 2,
          title: "Nike blazer mid 77 motivation",
          date: "04 April 2017",
          description:"Le géant du sportswear américain rend hommage à Ben Simmons au travers d’une Nike Blazer Mid ’77 Motivation inédite.",
          image: "https://www.lesitedelasneaker.com/wp-content/images/2020/04/nike-blazer-mid-77-motivation-01-1100x772.jpg"
        },
        {
          id: 3,
          title: "Air Jordan 1 mid euro tour",
          date: "22 March 2017",
          description: "La Air Jordan 1 Mid Euro Tour est issue de la collection 'Swoosh On Tour 2020'.",
          image: "https://www.lesitedelasneaker.com/wp-content/images/2020/05/air-jordan-1-mid-euro-tour-swoosh-on-tour-2020-cw7589-100-1-1.jpg"
        },
        {
          id: 4,
          title: "New Balance 992 Nimbus Cloud",
          date: "12 February 2017",
          description: "La classique New Balance 992 Nimbus Cloud fait son retour pour le printemps.",
          image: "https://www.lesitedelasneaker.com/wp-content/images/2020/05/new-balance-992-nimbus-cloud-1.jpg"
        },
        {
          id: 5,
          title: "Nike Air Max 90 DIY Flare",
          date: "25 January 2017",
          description: "L'équipementier américain continue de proposer des éditions ludiques à personnaliser, prochaine étape sur la liste, la Nike Air Max 90 DIY Flare.",
          image: "https://www.lesitedelasneaker.com/wp-content/images/2020/05/nike-air-max-90-diy-flare-cw5569-100-01-1100x772.jpg"
        }
      ]
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
  width: 256px;
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
