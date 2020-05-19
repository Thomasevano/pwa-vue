<template>
  <div class="home">
    <div class="last-article">
      <article class="media">
        <figure>
          <img
            src="http://via.placeholder.com/250x250"
            alt=""
          >
        </figure>
        <h2>Air jordan</h2>
        <p>Air jordan</p>
      </article>
      <div class="button">
        <router-link :to="'article/' + post.id">Lire l'article</router-link>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
}
</script>
