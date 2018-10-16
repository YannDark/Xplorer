<template>
  <b-container fluid class="h-75">
    <b-row class="h-100">
      <b-col cols='3'>
        <b-nav vertical pill class="">
          <b-nav-item active>Feu</b-nav-item>
          <b-nav-item active>Camping</b-nav-item>
          <b-nav-item>Toilettes publiques</b-nav-item>
        </b-nav>
      </b-col>
      <b-col cols='9'>
        <GmapMap
          :center="center"
          :zoom="zoom"
          style="width: 100%; height: 100%"
        >
          <GmapMarker
            :key="index"
            v-for="(m, index) in markers"
            :position="m.position"
            :clickable="true"
            @click="center=m.position"
          />
        </GmapMap>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import axios from 'axios'

export default {
  name: 'GoogleMap',
  props: {
    msg: String
  },
  data() {
    return {
      center : {lat: 0, lng: 0},
      zoom : 12,
      markers: [{position: {lat: 47.1881426, lng: -1.5368034}}]
    }
  },
  mounted () {
    // on récupère la position du user
    if(navigator.geolocation){
       navigator.geolocation.getCurrentPosition(position => {
        this.center = {lat: position.coords.latitude, lng: position.coords.longitude}
        console.log(position.coords)
      })
    }

    axios.get('https://data.nantesmetropole.fr/api/records/1.0/search/?dataset=244400404_toilettes-publiques-nantes-metropole&facet=commune&facet=pole&facet=type&facet=automatique&facet=acces_pmr')
    .then(function(data) {
      console.log(data)      
    }).catch(e => {
      console.log(e)
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
