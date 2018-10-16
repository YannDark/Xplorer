<template>
  <div id="app" >
    <b-nav justified fill tabs>
      <b-nav-item class="bg-success" active>Accueil</b-nav-item>
      <b-nav-item>Carte</b-nav-item>
      <b-nav-item>F.A.Q.</b-nav-item>
      <b-nav-item >Contact</b-nav-item>
    </b-nav>
    <!--<img alt="Vue logo" src="./assets/logo.png">-->
    <GoogleMap />
  </div>
</template>

<script>
import GoogleMap from './components/GoogleMap.vue'

export default {
  name: 'app',
  components: {
    GoogleMap
  }
}
</script>

<style>
html, body, #app {
  height: 100%;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>
