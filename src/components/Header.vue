<template>
  <header>
    <div class="header__container">
      <img class="burger__menu" src="../../public/img/burgermenu.svg" alt="">
      <img class="logo" src="../../public/img/logo.svg" alt="">
      <p class="language">FR | EN</p>
    </div>
    <nav class="nav">
      <router-link to="/">Accueil</router-link>
      <router-link to="/listing">Tous les articles</router-link>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style>
body {
  margin:0;
}

header {
  background-color: black;
  padding-top: 10px;
  padding-bottom: 10px;
}

.header__container {
  display: flex;
  justify-content: space-around;
  color: white;
}

.nav {
  display: none;
}

@media(min-width: 800px) {
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .header__container {
    justify-content: flex-start;
  }

  .logo {
    margin-left: 80px;
  }

  .language {
    margin-left: 15px;
    width: 53px;
  }

  .burger__menu {
    display: none;
  }

  .nav {
    display: block;
    margin-right: 80px;
    color: white;
    padding: 0;
  }

  .nav a {
    color: white;
    padding-left: 40px;
    text-decoration: none;
  }
}
</style>