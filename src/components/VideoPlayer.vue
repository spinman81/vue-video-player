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
  console.log("player:", player);
});

onBeforeUnmount(() => {
  player.dispose();
});

function onClick(e) {
  console.log("player:", player);
};
</script> 

<template>
  <div>
    <video id="videoPlayer" class="video-js"></video>
    <!-- <br></br>
    <button @click="onClick">Click</button> -->
  </div>
</template>
