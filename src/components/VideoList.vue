<template>
  <ul>
    <VideoListItem v-for="video in videos" :video="video" :key="video.id">

    </VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from './VideoListItem'

export default {
  name: 'VideoList',
  components: {
    VideoListItem
  },
  props: {
    videos: Array
  }
}
</script>

<style>
</style>
