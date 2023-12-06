<template>
  <v-app :style="{ background: backc }">
    <Header />
    <Main />
  </v-app>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  components: {
    Header,
    Main,
  },
  data() {
    return {
      backc: "#ECEFF1",
    };
  },
};
</script>
