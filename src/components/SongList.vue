<template>
  <section @click="song_clicked">
    <h3>{{ song_name }}</h3>
    <h3>{{ song_artist }}</h3>
  </section>
</template>

<script>
export default {
  name: "song-list",
  methods: {
    song_clicked() {
      this.$emit("songlist_clicked", this.song_selected);
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