<template>
  <div class="container">
    <search-bar @termChange="onTermChanged"></search-bar>
    <div class="row">
      <video-detail class="col-md-8 detail" :video="selectedVideo"></video-detail>
      <video-list class="col-md-4 list" :videos="videos" @videoSelect="onVideoSelected"></video-list>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';

const API_KEY='AIzaSyAe6uzzviFlXCau38c6NW63WuiqpQ-KO9k';

export default {
  name: "app",
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos: [],
      selectedVideo: null
    }
  },
  methods: {
    onTermChanged(term) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          maxResults: 15,
          q: term
        }
      })
      .then(response => {
        this.videos = response.data.items;
      })
      .catch(err => console.error(err));
    },

    onVideoSelected(video) {
      this.selectedVideo = video;
    }
  }
};
</script>

<style scoped>
  .list {
    height: 700px;
    overflow: scroll;
  }

  .detail {
    height: fit-content;
  }
</style>

