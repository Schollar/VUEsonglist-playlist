<template>
  <div>
    <section @click="playlist_song_clicked">
      <h3>{{ song.song_name }}</h3>
      <h3>{{ song.song_artist }}</h3>
    </section>
  </div>
</template>

<script>
// Same as the songlist page, we display our data sent to us from the parent above, and we also send data back to the parent when the object(song) is clicked. Im fairly certain this is how it works.
export default {
  name: "play-list",
  methods: {
    playlist_song_clicked() {
      this.$emit("playlist_song_clicked", this.song);
    },
  },
  props: {
    song: Object,
  },
};
</script>

<style scoped>
</style>