<template>
  <div
    :style="{
      backgroundColor: mainc,
      'font-size': fontSize + 'px',
      color: backc,
      padding: padSize + 'px',
    }"
    class="d-flex justify-center ml-n4"
  >
    <div class="mb-n1">
      <v-btn
        :icon="mdiGithub"
        :color="mainc"
        class="mt-n1 mr-n2"
        flat
        :href="url"
      ></v-btn>
      {{ title }}
    </div>
  </div>
</template>

<script>
import { mdiGithub } from "@mdi/js";

export default {
  data() {
    return {
      title: "7 Days to End with You Translator",
      mainc: "#00425A",
      backc: "#ECEFF1",
      fontSize: "22",
      padSize: "8",
      mdiGithub,
      url: "https://github.com/kdingn/7-days-to-end-with-you",
    };
  },
};
</script>
