<template>
  <div>
    <section @click="playlist_song_clicked">
      <h3>{{ song_name }}</h3>
      <h3>{{ song_artist }}</h3>
    </section>
  </div>
</template>

<script>
// Same as the songlist page, we display our data sent to us from the parent above, and we also send data back to the parent when the object(song) is clicked. Im fairly certain this is how it works.
export default {
  name: "play-list",
  methods: {
    playlist_song_clicked() {
      this.$emit("playlist_song_clicked", this.playlist_song_selected);
    },
  },
  data() {
    return {
      playlist_song_selected: {
        song_name: this.song_name,
        song_artist: this.song_artist,
        song_id: this.song_id,
      },
    };
  },
  props: {
    song_name: String,
    song_artist: String,
    song_id: Number,
  },
};
</script>

<style scoped>
</style>