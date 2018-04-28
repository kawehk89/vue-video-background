<template>
  <div>
    <video playsinline autoplay muted loop :poster="poster" class="background-vid">
      <source :src="videoSrcWebm" type="video/webm">
      <source :src="videoSrcMp4" type="video/mp4">
    </video>
    <div class="text-overlay" v-if="textOverlay">
      <div class="text-container">
        <h1 v-text="textHeadline"></h1>
        <h2 v-text="textSubtitle"></h2>
        <a :href="mainButtonUrl" class="main-button" v-smooth-scroll="{ duration: 1000, offset: -50}">{{ mainButtonLabel }}</a>
        <a :href="secondaryButtonUrl" class="secondary-button">{{ secondaryButtonLabel }}</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    videoSrcWebm: {
      default: '',
      type: String
    },
    videoSrcMp4: {
      default: '',
      type: String
    },
    poster: {
      default: '',
      default: String
    },
    textOverlay: {
      default: false,
      type: Boolean
    },
    textHeadline: {
      default: '',
      type: String
    },
    textSubtitle: {
      default: '',
      type: String
    },
    textBody: {
      default: '',
      type: String
    },
    mainButtonUrl: {
      default: '',
      type: String
    },
    mainButtonLabel: {
      default: '',
      type: String
    },
    secondaryButtonUrl: {
      default: '',
      type: String
    },
    secondaryButtonLabel: {
      default: '',
      type: String
    }
  }
}
</script>

<style lang="css" scoped>
  .background-vid {
      position: absolute;
      top: 50%;
      left: 50%;
      min-height: 100%;
      width: 100%;
      height: auto;
      object-fit: cover;
      z-index: -100;
      transform: translateX(-50%) translateY(-50%);
  }
  .text-container {
    text-align: center;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  .text-overlay {
    font-weight:100;
    background: #1f253896;;
    color: white;
    padding: 2rem;
    width: 100%;
    float: right;
    font-size: 1.2rem;
    min-height: 800px;
  }
  .text-overlay h1 {
    color: #fff;
    font-size: 38px;
  }
  .text-overlay h2 {
    font-size: 24px;
    font-family: "Roboto", "Helvetica", "Arial", sans-serif;
    font-weight: 300;
    color: #fff;
    padding-bottom: 15px;
  }
  .text-overlay p {
    font-size: 14px;
  }
</style>
