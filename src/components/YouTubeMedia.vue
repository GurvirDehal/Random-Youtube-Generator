<template lang="pug">
    iframe(id="ytplayer"
           width="560" 
           height="315" 
           :src="videoUrl"
           frameborder="0" 
           allow="autoplay; encrypted-media"
           allowfullscreen)
</template>

<script>
  // var tag = document.createElement('script');
  // tag.src = "//www.youtube.com/iframe_api";
  // var firstScriptTag = document.getElementsByTagName('script')[0];
  // firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);
  // var player

  // function onYouTubeIframeAPIReady() {
  //     player = new YT.Player('ytplayer_1-5', {events: {'onReady': onPlayerReady}});
  // }

  // function onPlayerReady(event) {
  //     event.target.playVideo();
  // }

export default {
    props: {
      videoId: {
        type: String,
        default: ''
      }
    },
    computed: {
      videoUrl: function() {
        return `https://www.youtube.com/embed/${this.videoId}?autoplay=1`
      }
    }
}
</script>

<style lang="scss" scoped>

</style>