<template>
  <div id="#app" class="container">
    <searchBar @termChange="onTermChange" />
    <div class="row">
      <videoDetail :video="selectVideo" />
      <videoList @onVideoSelect="onVideoSelect" :videos="videos"></videoList>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import searchBar from "./components/SearchBar";
import videoList from "./components/VideoList";
import videoDetail from "./components/VideoDetail";

const API_KEY = "AIzaSyB6_8BOv6x_DuBVXM6i8rcbZ4iHxsfjdRk";

export default {
  name: "app",
  components: {
    searchBar,
    videoList,
    videoDetail
  },
  methods: {
    onTermChange(changeTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: changeTerm
          }
        })
        .then(res => {
          this.videos = res.data.items;
        });
    },
    onVideoSelect(video) {
      this.selectVideo = video;
    }
  },
  data() {
    return {
      videos: [],
      selectVideo: null
    };
  }
};
</script>

<style>
/* #app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
