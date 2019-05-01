<template lang="pug">
  #app
    img.vue-logo(src='./assets/logo.png')

    select(v-model="selectedCountry")
      option(v-for="(country, index) in countries" :key="index" v-bind:value="country.value")| {{country.name}}
    
    spinner(v-show="showSpinner")
    
    ul(v-show="!showSpinner")
      artist(v-for="artist in artists" v-bind:artist="artist")
</template>

<script>
import getArtists from './api'
import Artist from './components/Artist.vue'
import Spinner from './components/Spinner.vue'

export default {
  name: 'app',
  data () {
    return {
      artists: [],
      countries: [
        {name: "Argentina", value: "argentina"},
        {name: "Venezuela", value: "venezuela"},
        {name: "España", value: "spain"},
        {name: "Colombia", value: "colombia"},
      ],
      selectedCountry: "argentina",
      showSpinner: false
    }
  },
  components:{
    Artist,
    Spinner
  },
  methods: {
    refreshArtists(){
      const self = this
      self.showSpinner = true;    
      getArtists(this.selectedCountry)
        .then(function(artists){
          self.artists = artists; 
          self.showSpinner = false;
        });  
    }
  },
  mounted: function(){
    this.refreshArtists()
  },
  watch:{
    selectedCountry(){
      this.refreshArtists()
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

select{
  display: block;
  margin: auto;
}

.vue-logo{
  display: block;
  margin: auto;
}
</style>
