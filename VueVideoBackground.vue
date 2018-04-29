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
        <a v-if="mainButtonUrl && mainButtonLabel" :href="mainButtonUrl" class="main-button" v-smooth-scroll="{ duration: 1000, offset: -50}">{{ mainButtonLabel }}</a>
        <a v-if="secondaryButtonUrl && secondaryButtonLabel" :href="secondaryButtonUrl" class="secondary-button">{{ secondaryButtonLabel }}</a>
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
    },
    overlayColor: {
      default: '#1f253800',
      type: String
    }
  },
  computed: {
    cssProps() { return {
        '--overlay-color': this.overlayColor,
      }
    }
	}
}
</script>

<style lang="css" scoped>
@media (max-width: 400px) {
  .background-vid, .text-overlay {
    height: 600px;
  }

  .text-container {
    top: 40%;
  }
}

@media (min-width: 660px) {
  .background-vid, .text-overlay {
    height: 400px;
  }

  .text-container {
    top: 50%;
  }
}

@media (min-width: 769px) {
  .background-vid, .text-overlay {
    height: 800px;
  }
}

  .background-vid {
    width: 100%;
    object-fit: cover;
    z-index: -100;
  }
  .text-container {
    text-align: center;
    position: absolute;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  .text-overlay {
    font-weight:100;
    background: var(--overlay-color);
    color: white;
    width: 100%;
    position: absolute; top: 0; left: 0;
    font-size: 1.2rem;
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
