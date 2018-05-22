<template>
  <main>
    <SearchBar @termChange="onTermChange" />
    <VideoList :videos="videos" />
  </main>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'

const API_KEY = 'AIzaSyAgZd-DsanSWFghvFGLU_hIk7Ef4mrAkCo'

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList
  },
  data() {
    return {
      videos: []
    }
  },
  methods: {
    async onTermChange(searchTerm) {
      const res = await axios.get(
        'https://www.googleapis.com/youtube/v3/search',
        {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm
          }
        }
      )
      this.videos = res.data.items
    }
  }
}
</script>
