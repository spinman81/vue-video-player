<script setup>
import { ref } from "vue";
import { NButton, NInput, NInputGroup, NDivider, NFlex } from "naive-ui";
import { NConfigProvider, NGlobalStyle } from 'naive-ui';
import { darkTheme } from 'naive-ui';

import VideoPlayer from "./components/VideoPlayer.vue";

// https://www.etvnet.com/watch/karaoke-klab-2-vyipusk/2585486
const url = ref("https://195181171156.cdn.etvnet.com/vod/OBnNsIrx8oSft6peemu2tEgcOmLidXCONzrk0eNoWlbtsN_-3Yd1bo9NRuESlJ7SDK2ZqCAv77H7g57dkH0CGQ/playlist.m3u8");
const playerOptions = {
  autoplay: false,
  controls: true,
  muted: true,
  width: 960,
  sources: [
    {
      src: url.value,
      type: "application/x-mpegURL",
    },
  ],
};
</script>

<template>
  <n-config-provider :theme="darkTheme">
    <n-global-style />
    <div class="wrap">
      <n-input-group>
        <n-button type="primary">Play Stream</n-button>
        <n-input :placeholder="url" clearable></n-input>
        <n-button type="primary" ghost>Play</n-button>
      </n-input-group>
      <n-divider ></n-divider>
    </div>
    <n-flex justify="center">
      <video-player
        class="vjs-custom-skin"
        :options="playerOptions"
      />
    </n-flex>
    <n-divider ></n-divider>
  </n-config-provider>
</template>

<style scoped>
div.wrap {
  width: 98%;
  margin: auto;
  margin-top: 10px;
}
</style>

