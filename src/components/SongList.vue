<template>
  <section @click="song_clicked">
    <h3>{{ song.song_name }}</h3>
    <h3>{{ song.song_artist }}</h3>
  </section>
</template>

<script>
// Not a whole lot going on here, we have our props sent to us from the parent, we display them above, but then we also have an object we use to send back to the parent when that particular
// object(song) is clicked.
export default {
  name: "song-list",
  methods: {
    song_clicked() {
      this.$emit("songlist_clicked", this.song);
    },
  },
  props: {
    song: Object,
  },
};
</script>

<style scoped>
</style>