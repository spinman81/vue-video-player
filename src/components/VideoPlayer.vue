<script setup>
import videojs from 'video.js';
import { onBeforeUnmount, onMounted } from "vue";
import "video.js/dist/video-js.css";
const props = defineProps({
  options: {
    type: Object,
    default: {}
  }
});

let player = null;
onMounted(() => {
  player = videojs("videoPlayer", props.options, () => {
    console.log("[VideoPlayer] ready!");
  });
});

onBeforeUnmount(() => {
  player.dispose();
});
</script> 

<template>
  <div>
    <video id="videoPlayer" class="video-js"></video>
  </div>
</template>
