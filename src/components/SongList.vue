<template>
  <section @click="song_clicked">
    <h1>{{ song_name }}</h1>
    <h1>{{ song_artist }}</h1>
  </section>
</template>

<script>
export default {
  name: "song-list",
  methods: {
    song_clicked() {
      this.$emit("song_clicked", this.song_selected);
    },
  },
  props: {
    song_name: String,
    song_artist: String,
    song_id: Number,
  },
  data() {
    return {
      song_selected: {
        song_name: this.song_name,
        song_artist: this.song_artist,
        song_id: this.song_id,
      },
    };
  },
};
</script>

<style scoped>
</style>