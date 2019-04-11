<template lang="pug">
  li.artist
    img(:src="artist.image[2]['#text']")
    h2: a(:href="artist.url" target="_blank") {{ artist.name }}
</template>

<script>
export default {
  name: 'artist',
  props: [ 'artist' ]
}
</script>

<style lang="stylus" scoped>
li.artist
  display block
  margin 10px 0
</style>
