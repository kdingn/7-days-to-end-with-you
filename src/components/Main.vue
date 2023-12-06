<template>
  <div class="d-flex justify-center">
    <v-card :width="cardSize">
      <v-row class="d-flex justify-center my-2">
        <div v-for="n in nalphabet" :key="n" class="mx-1">
          <img
            :src="imagePath(idxn(n))"
            :width="imgSize"
            style="
               {
                border: solid;
              }
            "
          />
        </div>
      </v-row>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nalphabet: 26,
      imgSize: 80,
      cardSize: 550,
    };
  },
  methods: {
    idxn(n) {
      return n - 1;
    },
    imagePath(x) {
      return new URL(`/src/assets/${x}.png`, import.meta.url).href;
    },
  },
};
</script>
