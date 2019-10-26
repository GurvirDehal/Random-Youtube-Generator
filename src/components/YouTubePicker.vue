<template lang="pug">
    #YouTubeGen
        h1 Random YouTube Generator
        button(@click="getRandomWord") Click Me
        you-tube-media(v-if="videoId" :videoId="videoId")
    </div>
</template>

<script>
import YouTubeMedia from './YouTubeMedia'
export default {
  components: {
      YouTubeMedia
  },
  props: {

  },
  data: function() {
      return {
          word: '',
          videoId: '',
      }
  },
  methods: {
      async getRandomWord() {
          const response = await fetch(`http://api.wordnik.com/v4/words.json/randomWord?api_key=${process.env.VUE_APP_WORDNIK}`)
          const myJson = await response.json()
          this.word = myJson.word
          this.getVideo(this.word)
      },
      async getVideo(query) {
          const response = await fetch(`https://www.googleapis.com/youtube/v3/search?part=snippet&q=${query}&type=video&key=${process.env.VUE_APP_API_KEY}`)
          const myJson = await response.json()
          this.videoId = myJson.items[0].id.videoId
      }
  }
}
</script>

<style scoped>
#YouTubeGen {
    display: flex;
    flex-direction: column;
}

button {
    width: fit-content;
    margin-bottom: 20px;
}
</style>
