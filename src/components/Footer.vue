<template>
  <footer>
    <div class="newsletter">
      <h2>Plus de Neostreet ?</h2>
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
* {
  margin: 0;
  padding: 0;
}

footer {
  margin-top: 40px;
}

.newsletter {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: 'Futura book';
  margin-bottom: 20px;
}

.newsletter h2 {
  font-weight: bold;
  font-size: 2rem;
  text-transform: uppercase;
  text-align: center;
  margin-bottom: 10px;
}

a {
  color: black;
  font-weight: bold;
}

.footer {
  font-family: 'Futura book';
  background-color: black;
  color:white;
  padding: 20px 0px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.footer img {
  margin-bottom: 20px;
}

.footer__link {
  display: flex;
  justify-content: space-around;
  font-weight: bold;
  font-size: 14px;
  width: 100%;
  margin-bottom: 20px;
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

</style>