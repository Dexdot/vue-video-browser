<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <img class="mr-3" :src="url" :alt="title">
    <div class="media-body">{{ title }}</div>
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: {
    video: Object
  },
  methods: {
    onVideoSelect() {
      this.$emit('videoSelect', this.video);
    }
  },
  computed: {
    title() {
      return this.video.snippet.title;
    },
    url() {
      return this.video.snippet.thumbnails.default.url;
    }
  }
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
  transition: 0.2s ease-in-out;
}
li:hover {
  background: #f8f8f8;
}
</style>

