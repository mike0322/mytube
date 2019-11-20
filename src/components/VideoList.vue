<template>
  <ul class="list-group col-lg-4">
    <videoItem
      @onVideoSelect="onVideoSelect"
      v-for="video in videos"
      :key="video.etag"
      :video="video"
    ></videoItem>
  </ul>
</template>


<script>
import videoItem from "./VideoItem";

export default {
  name: "VideoList",
  props: ["videos"],
  components: {
    videoItem
  },
  methods: {
    onVideoSelect(video) {
      this.$emit("onVideoSelect", video);
    }
  }
};
</script>