<template>
    <div id = "YoutubeGen">
        <h1> Random YouTube Generator </h1>
        <button @click="getRandomWord"> Text </button>
        <p> {{ word }} </p>
    </div>
</template>

<script>
export default {
  props: {
      lol: Function
  },
  data: function() {
      return {
          word: ''
      }
  },
  methods: {
      async getRandomWord() {
          const response = await fetch('https://random-word-api.herokuapp.com/word?key=6RS9GK59&number=1')
          const myJson = await response.json()
          this.word = myJson[0]
      }
  }
}
</script>

<style scoped>

</style>
