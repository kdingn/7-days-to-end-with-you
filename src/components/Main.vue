<template>
  <div>
    <v-row v-for="j in this.nrow" :key="j">
      <v-col v-for="i in this.ncol" :key="i + this.ncol * j">
        <div v-if="idxIJ(i, j) < this.nalphabet">
          <v-img :src="imagePath(idxIJ(i, j))"></v-img>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ncol: 6,
      nalphabet: 26,
    };
  },
  computed: {
    nrow() {
      return parseInt(this.nalphabet / this.ncol + 1);
    },
  },
  methods: {
    idxIJ(i, j) {
      return i + this.ncol * (j - 1) - 1;
    },
    imagePath(x) {
      return "/src/assets/" + x + ".png";
    },
  },
};
</script>
