<template lang="pug">
  #app
    img(src='./assets/logo.png')
    h1 PlatziMusic
    ul
      artists(:artists="artists")    
</template>

<script>
import Artists from './components/Artists.vue';
import getArtists from './api';

export default {
  name: 'app',
  components: {
    Artists,
  },
  data () {
    return {
      artists: []
    }
  },
  mounted: function() {
    const self = this;
    getArtists()
      .then(
        function(artists) {
          self.artists = artists;
        }
      )
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
