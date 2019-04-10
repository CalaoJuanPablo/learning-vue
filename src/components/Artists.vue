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
  padding 0
a 
  color #42b983
</style>
