<template>
  <div>
    <song-list
      v-for="song in song_list"
      :key="song.song_id"
      :song_artist="song.song_artist"
      :song_name="song.song_name"
      :song_id="song.song_id"
      @song_clicked="song_was_clicked"
    ></song-list>
    <play-list
      v-for="user_song in user_song_list"
      :key="user_song.song_id"
      :user_song_list="user_song"
      :song_id="user_song.id"
      :song_name="user_song.song_name"
      :song_artist="user_song.song_artist"
    ></play-list>
  </div>
</template>

<script>
import SongList from "./SongList.vue";
import PlayList from "./PlayList.vue";
export default {
  name: "page-body",
  methods: {
    song_was_clicked(payload) {
      console.log(payload);
      this.user_song_list.push(payload);
      this.remove_song(payload);
    },
    remove_song(ob) {
      var song_id_selected = ob.song_id;
      for (var i = 0; i < this.song_list.length; i++) {
        if (song_id_selected === this.song_list[i].song_id) {
          this.song_list.splice(i, 1);
        }
      }
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