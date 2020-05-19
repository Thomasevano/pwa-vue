<template>
  <footer>
    <div class="newsletter">
      <h2>Plus de Neostreet</h2>
      <p>Inscrivez-vous à la newsletter</p>
      <a href="">S'inscrire</a>
    </div>
    <div class="footer">
      <img src="../../public/img/logo.svg" alt="">
      <div class="footer__link">
        <p>À propos</p>
        <p>C.G.U</p>
        <p>Partenaires</p>
        <p>Contact</p>
      </div>
      <div class="footer__copyright">
        <p>© 2020 Neostreet</p>
      </div>
    </div>
    
  </footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style scoped>
.newsletter {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

a {
  color: black;
  font-weight: bold;
}

.footer {
  margin-top: 32px;
  background-color: black;
  color:white;
  padding-top: 8px;
  padding-bottom: 8px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.footer__link {
  display: flex;
  justify-content: space-around;
  font-weight: bold;
  font-size: 14px;
  width: 100%;
}

.footer__copyright p {
  margin: 0;
}

@media(min-width: 1000px) {
 .footer__link {
   font-size: 16px;
   width: 30%;
 }
}

@media(min-width: 1366px) {
  .newsletter {
    margin-left: 183px;
  }
}

</style>