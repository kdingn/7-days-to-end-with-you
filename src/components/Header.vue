<template>
  <div
    :style="{
      backgroundColor: mainc,
      'font-size': fontSize + 'px',
      color: backc,
      padding: padSize + 'px',
    }"
    class="d-flex justify-center"
  >
    <v-btn
      :icon="mdiGithub"
      :color="mainc"
      class="mt-n2"
      flat
      :href="url"
    ></v-btn>
    {{ title }}
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
      marginLeft: -140,
      url: "https://github.com/kdingn/7-days-to-end-with-you",
    };
  },
};
</script>
