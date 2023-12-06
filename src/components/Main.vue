<template>
  <div class="d-flex justify-center">
    <!-- <v-card width="600" class="d-flex justify-center"> -->
    <v-card :width="cardSize">
      <v-row v-for="j in nrow" :key="j" no-gutters>
        <v-col v-for="i in ncol" :key="i + ncol * j">
          <div v-if="idxIJ(i, j) < nalphabet">
            <v-img :src="imagePath(idxIJ(i, j))" :width="imgSize"></v-img>
          </div>
        </v-col>
      </v-row>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ncol: 6,
      nalphabet: 26,
      imgSize: 80,
    };
  },
  computed: {
    nrow() {
      return parseInt(this.nalphabet / this.ncol + 1);
    },
    cardSize() {
      return this.ncol * this.imgSize;
    },
  },
  methods: {
    idxIJ(i, j) {
      return i + this.ncol * (j - 1) - 1;
    },
    imagePath(x) {
      return new URL(`/src/assets/${x}.png`, import.meta.url).href;
    },
  },
};
</script>
