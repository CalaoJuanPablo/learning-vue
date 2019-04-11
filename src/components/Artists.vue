<template lang="pug">
  ul
    artist(v-for="artist in artists" :artist="artist" :key="artist.mbid")
</template>

<script>
import Artist from './Artist.vue'
import getArtists from '../api';

export default {
  name: 'artists',
  components: {
    Artist,
  },
  props: [ 'artists' ]
}
</script>

<style lang="stylus">
ul 
  list-style-type none
  max-width 1200px
  margin 50px auto
  padding 0
  display grid
  grid-template-columns repeat(auto-fill, minmax(180px, 1fr))
  grid-gap 20px
a 
  color #42b983
</style>
