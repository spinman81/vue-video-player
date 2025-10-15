<script setup>
import { ref } from "vue";
import { NMenu, NDivider, NFlex } from "naive-ui";
import { mainMenuOptions } from "@/modules/menu-options.mjs";

const activeKey = ref(null);

function handleKeyUpdate(key, item) {
  activeKey.value = null;
}
</script>

<template>
  <n-flex justify="end">
    <div class="wrap">
      <n-menu
        v-model:value="activeKey"
        :options="mainMenuOptions"
        @update:value="handleKeyUpdate"
        horizontal
      ></n-menu>
    </div>
  </n-flex>
  <n-divider></n-divider>
</template>

<style scoped>
.n-menu {
  width: 10rem;
  margin: auto;
  align-items: end;
}

.n-divider {
  margin-top: 0px;
}
</style>