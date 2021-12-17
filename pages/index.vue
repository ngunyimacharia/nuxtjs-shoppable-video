<template>
  <video
    id="video-player"
    controls
    muted
    class="cld-video-player cld-video-player-skin-dark w-2/3 h-96 mx-auto"
  >
  </video>
</template>

<script>
export default {
  name: 'IndexPage',
  data(){
    return {
      cld:null,
      player:null,
      source:"nuxtjs-shoppable-video/pexels-diva-plavalaguna-6192939.mp4"
    };
  },
  mounted(){
    this.cld = cloudinary.Cloudinary.new({ cloud_name: process.env.NUXT_ENV_CLOUDINARY_CLOUD_NAME });

    this.player = this.cld.videoPlayer('video-player');

    this.player.source(this.source);
  }
}
</script>
