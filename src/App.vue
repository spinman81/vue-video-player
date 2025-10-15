<script setup>
import { ref, computed } from "vue";
import { NButton, NInput, NInputGroup, NDivider, NFlex } from "naive-ui";
import { NConfigProvider, NGlobalStyle } from 'naive-ui';
import { darkTheme } from 'naive-ui';

import Menu from "@/components/Menu.vue";
import VideoPlayer from "@/components/VideoPlayer.vue";

// https://www.etvnet.com/watch/karaoke-klab-2-vyipusk/2585486
const url = ref("https://195181171156.cdn.etvnet.com/vod/nEBds7GWdD7moa-Sd1VG8EsWkExDZSAxgjQSw2ylU_rIYlyokqScwempNy1DcQ7eLXxNN84Eg9DluS2gKIy92w/playlist.m3u8");
// const url = ref("https://vb-rtb-temp.uma.media/1758394625/mQ0W2FwZonkyT3v8puWtww/vod/vod:premier/6d3973e1bfe04a9eaeab33dee793cca2.m3u8?streams=67864096-b2e8-4664-a7fb-e7615646bc46:w:1920:h:1072:vb:4499968:ab:192000:d:1448600:vc:avc1.640029:ac:mp4a.40.2,f493a687-3955-4ec9-876b-66dd818883d4:w:1280:h:720:vb:2967317:ab:128001:d:1448600:vc:avc1.640029:ac:mp4a.40.2,bd57eca0-e7dc-49a3-83f2-5a493876173b:w:848:h:480:vb:1484914:ab:128001:d:1448600:vc:avc1.4d401f:ac:mp4a.40.2,2c47af4a-5d21-4e1e-ac31-289653e1b531:w:640:h:368:vb:1299968:ab:64005:d:1448600:vc:avc1.42c01f:ac:mp4a.40.2");

const playerOptions = {
  autoplay: false,
  controls: true,
  muted: true,
  width: computed(() => {return window.innerWidth * 0.5}).value,
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
      <!-- <Menu></Menu> -->
      <n-input-group>
        <n-button type="primary">Play Stream</n-button>
        <n-input :placeholder="url" clearable></n-input>
        <n-button type="primary" ghost>Play</n-button>
      </n-input-group>
      <n-divider ></n-divider>
    </div>
    <n-flex justify="center">
      <div class="container">
        <video-player
          class="vjs-custom-skin"
          :options="playerOptions"
        />
      </div>
    </n-flex>
    <!-- <n-divider ></n-divider> -->
  </n-config-provider>
</template>

<style scoped>
div.wrap {
  width: 98%;
  margin: auto;
  margin-top: 10px;
}

.container {
  border: 1px dotted;
  /* width: 50%; */
}
</style>

