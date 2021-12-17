<template>
  <div>
    <h1 class="my-10 block text-center leading-8 font-extrabold tracking-tight text-gray-600 text-2xl"> 
      How to create Shoppable videos in Nuxt.Js
    </h1>
    <video
      id="video-player"
      controls
      muted
      class="cld-video-player cld-video-player-skin-dark w-2/3 h-96 mx-auto"
    >
    </video>
    <div class="mt-6 prose prose-indigo prose-lg text-gray-500 mx-auto leading-10 w-2/3 mx-auto text-center">
      To shop the video, press on the cart icon on the top right section.
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data(){
    return {
      cld:null,
      player:null,
    };
  },
  mounted(){
    this.cld = cloudinary.Cloudinary.new({ cloud_name: process.env.NUXT_ENV_CLOUDINARY_CLOUD_NAME });

    this.player = this.cld.videoPlayer('video-player');

    this.player.source(
      "nuxtjs-shoppable-video/video.mp4",
      {
         shoppable: {    
            transformation: {
                crop: "pad",
                aspect_ratio: "1"
            },
            products: [
              {
                  productId: 1,
                  productName: "Macbook Pro",
                  startTime: 0,
                  endTime: 1,
                  publicId:
                  "nuxtjs-shoppable-video/macbook",
                  hotspots: [
                    {
                        time: "00:02",
                        x: "62%",
                        y: "32%",
                        tooltipPosition: "left",
                        clickUrl: "https://www.amazon.com/Apple-MacBook-Air-Retina-Display/dp/B08VF621Z4/ref=sr_1_2"
                    }
                  ],
                  onHover: {
                    action: "overlay",
                    args: "See the MacBook in the video"
                  },
                  onClick: {
                    action: "seek",
                    pause: 5,
                    args: {
                        time: "00:02"
                    }
                  }
              },
              {
                  productId: 2,
                  productName: "iPad Pro",
                  startTime: 0,
                  endTime: 1,
                  publicId:
                  "nuxtjs-shoppable-video/ipad",
                  hotspots: [
                    {
                        time: "00:02",
                        x: "55%",
                        y: "68%", 
                        tooltipPosition: "left",
                        clickUrl: "https://www.amazon.com/Apple-12-9-inch-Wi%E2%80%91Fi-Cellular-256GB/dp/B0932BB1BX/ref=sr_1_3"
                    }
                  ],
                  onHover: {
                    action: "overlay",
                    args: "See the iPad in the video"
                  },
                  onClick: {
                    action: "seek",
                    pause: 5,
                    args: {
                        time: "00:02"
                    }
                  }
              },
              {
                  productId: 3,
                  productName: "iPhone",
                  startTime: 0,
                  endTime: 1,
                  publicId:
                  "nuxtjs-shoppable-video/iphone",
                  hotspots: [
                    {
                        time: "00:02",
                        x: "35%",
                        y: "68%", 
                        tooltipPosition: "left",
                        clickUrl: "https://www.amazon.com/Apple-iPhone-12-Pro-Max/dp/B09JFS16CP/ref=sr_1_1"
                    }
                  ],
                  onHover: {
                    action: "overlay",
                    args: "See the iphone in the video"
                  },
                  onClick: {
                    action: "seek",
                    pause: 5,
                    args: {
                        time: "00:02"
                    }
                  }
              },
            ]
        }
      }
    );
  }
}
</script>

