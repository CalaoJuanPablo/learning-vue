<template lang="pug">
  #app
    img(src="./assets/logo.png")
    h1 PlatziMusic
    h3 Top LastFM artists by country.
    select(v-model="selectedCountry")
      option(v-for="country in countries" :value="country.value") {{ country.name }}
    spinner(v-show="loading")
    ul(v-show="!loading")
      artists(:artists="artists")    
</template>

<script>
import Artists from './components/Artists.vue';
import Spinner from './components/Spinner.vue';
import getArtists from './api';

export default {
  name: 'app',
  components: {
    Artists,
    Spinner,
  },
  data () {
    return {
      artists: [],
      countries: [
        {name: 'Argentina', value: 'argentina'},
        {name: 'Colombia', value: 'colombia'},
        {name: 'España', value: 'spain'}
      ],
      selectedCountry: 'colombia',
      loading: true
    }
  },
  mounted: function() {
    this.refreshArtist(this.selectedCountry)
  },
  methods: {
    refreshArtist(country) {
      const self = this;
      this.loading = true;
      getArtists(country)
        .then(function(artists) {
          self.artists = artists;
        })
        .then(function(){ self.loading = false })
    }
  },
  watch: {
    selectedCountry: function() {
      this.refreshArtist(this.selectedCountry)
    }
  }
}
</script>

<style lang="stylus">
  #app 
    font-family 'Avenir', Helvetica, Arial, sans-serif
    -webkit-font-smoothing antialiased
    -moz-osx-font-smoothing grayscale
    text-align center
    color #2c3e50
    margin-top 60px
    
  h1, h2 
    font-weight normal
</style>
