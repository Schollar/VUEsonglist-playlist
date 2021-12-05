<template>
  <div>
    <h1>{{ song_name }}</h1>
    <h1>{{ song_artist }}</h1>
  </div>
</template>

<script>
export default {
  name: "play-list",
  props: {
    user_song_list: Object,
    song_name: String,
    song_artist: String,
  },
};
</script>

<style scoped>
</style>