<template>
  <div>
    <h1>SONG LIST</h1>
    <!-- Using V-for to display the songs on the page and listening for our custom event also sending our data through to child components as they are expecting props. -->
    <song-list
      v-for="song in song_list"
      :key="song.song_id"
      :song="song"
      @songlist_clicked="song_was_clicked"
    ></song-list>
    <h1>PLAY LIST</h1>
    <!--Same as above -->
    <play-list
      v-for="user_song in user_song_list"
      :key="user_song.song_id"
      :song="user_song"
      @playlist_song_clicked="playlist_song_clicked"
    ></play-list>
  </div>
</template>

<script>
import SongList from "./SongList.vue";
import PlayList from "./PlayList.vue";
export default {
  name: "page-body",
  methods: {
    // Pushing the song clicked to the songlist array, and calling our remove playlist song function
    playlist_song_clicked(payload) {
      this.song_list.push(payload);
      this.remove_song(payload, this.user_song_list);
    },
    // Here we grab our song id that was clicked, and then we loop through the user song list and
    // check for a match in the user_song_list, if a match is found we remove the song from the user song list array
    remove_song(ob, arr) {
      var playlist_song_id_selected = ob.song_id;
      for (var i = 0; i < arr.length; i++) {
        if (playlist_song_id_selected === arr[i].song_id) {
          arr.splice(i, 1);
        }
      }
    },
    // These two functions are the same as above except for opposite. It pushes a song to the user_song_list array and the second function removes the song from the song list array
    // I feel like there is a better way to do all this, but since im still learning vue I fell back on my vanilla JS to get it done. It still works like it should(i think?) so overall very happy with it.
    // Once you can start wrapping your head around what your data is, where its coming from, how to manipulate it and send it back, I think vue can be super powerful.
    song_was_clicked(payload) {
      this.user_song_list.push(payload);
      this.remove_song(payload, this.song_list);
    },
  },
  data() {
    return {
      user_song_list: [],
      song_list: [
        {
          song_name: "First Song",
          song_artist: "First Artist",
          song_id: 1,
        },

        {
          song_name: "Second Song",
          song_artist: "Second Artist",
          song_id: 2,
        },

        {
          song_name: "Third Song",
          song_artist: "Third Artist",
          song_id: 3,
        },
      ],
    };
  },
  components: {
    SongList,
    PlayList,
  },
};
</script>

<style scoped>
</style>