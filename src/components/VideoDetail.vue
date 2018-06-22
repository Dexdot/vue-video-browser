<template>
  <div class="col-md-8" v-if="video">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe class="embed-responsive-item" :src="videoUrl" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
    </div>
    <div class="details">
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VideoDetail',
  props: {
    video: Object
  },
  computed: {
    videoUrl() {
      return `https://youtube.com/embed/${this.video.id.videoId}`;
    }
  }
};
</script>


<style scoped>
.details {
  margin-top: 8px;
  padding: 8px;
  border-radius: 4px;
  border: 1px solid #ddd;
}
</style>
