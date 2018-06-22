<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoDetail :video="selectedVideo"></VideoDetail>
    <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
  </div>
</template>

<script>
import axios from 'axios';

import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';

const API_KEY = 'AIzaSyDSUn2v_bL3XZPN3BtiXwwoQBJT8zcYKt4';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data: () => ({
    videos: [],
    selectedVideo: {}
  }),
  methods: {
    onTermChange(searchTerm) {
      const params = {
        key: API_KEY,
        type: 'video',
        part: 'snippet',
        q: searchTerm
      };

      axios
        .get('https://www.googleapis.com/youtube/v3/search', { params })
        .then(response => (this.videos = response.data.items));
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
};
</script>
