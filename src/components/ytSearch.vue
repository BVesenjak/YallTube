<template>
  <div>
    <input type="text" v-model="searchQuery" placeholder="Search YouTube" @keyup.enter="searchVideos">
    <button @click="searchVideos">Search</button>
    <div v-for="video in videos" :key="video.id.videoId" class="video-result">
      <iframe width="560" height="315" :src="videoUrl(video.id.videoId)" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>
  </div>
</template>



<script>
import axios from 'axios';

export default {
  data() {
    return {
      searchQuery: '',
      videos: []
    };
  },
  methods: {
    searchVideos() {
      const apiKey = '27130d7900msh2cad033a2b3bd7ap16a400jsnbc154a043234';
      const apiHost = 'youtube-v31.p.rapidapi.com';
      const url = `https://${apiHost}/search`;
      
      axios.get(url, {
        params: {
          part: 'snippet',
          q: this.searchQuery,
          type: 'video'
        },
        headers: {
          'x-rapidapi-key': apiKey,
          'x-rapidapi-host': apiHost
        }
      })
      .then(response => {
        this.videos = response.data.items;
      })
      .catch(error => {
        console.error('Error fetching YouTube videos:', error);
      });
    },
    videoUrl(videoId) {
      return `https://www.youtube.com/embed/${videoId}`;
    }
  }
}
</script>
