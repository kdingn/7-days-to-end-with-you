<template>
  <div class="d-flex justify-center my-2">
    <v-card :width="cardSize" :height="imgSize * 0.7">
      <div class="mx-1">
        <v-row class="ml-0">
          <div v-for="n in nlist" :key="n + 'list'">
            <img
              :src="imagePath(idxn(n))"
              :width="imgSize * 0.5"
              class="mt-5 mb-3 ml-2"
            />
          </div>
          <v-spacer />
          <v-btn
            :icon="mdiChevronLeft"
            class="mt-4 mr-2"
            variant="text"
            @click="reduceNlist"
          ></v-btn>
        </v-row></div
    ></v-card>
  </div>
  <div class="d-flex justify-center mb-2">
    <v-card :width="cardSize" :min-height="imgSize * 0.35">
      <div class="d-flex justify-center">
        <div v-for="i in 7" :key="i + 'word'">
          <span v-if="nword[i - 1]" class="text-orange-darken-4">
            {{ translated[i - 1] }}
          </span>
          <span v-else>{{ translated[i - 1] }}</span>
          <span v-if="i != 7">,&nbsp;</span>
        </div>
      </div>
    </v-card>
  </div>
  <div class="d-flex justify-center">
    <v-card :width="cardSize">
      <v-row class="d-flex justify-center my-2">
        <div v-for="n in nalphabet" :key="n + 'char'" class="mx-1">
          <img
            :src="imagePath(idxn(n))"
            :width="imgSize"
            @click="addNlist(n)"
            class="shadow"
          />
        </div>
      </v-row>
    </v-card>
  </div>
</template>

<script>
import { mdiChevronLeft } from "@mdi/js";

let initialNword = {
  0: false,
  1: false,
  2: false,
  3: false,
  4: false,
  5: false,
  6: false,
};

export default {
  data() {
    return {
      nalphabet: 26,
      imgSize: 80,
      cardSize: 550,
      mdiChevronLeft,
      nlist: [10, 12, 25, 8],
      alphabets: [..."abcdefghijklmnopqrstuvwxyz"],
      nword: initialNword,
    };
  },
  methods: {
    idxn(n) {
      return n - 1;
    },
    imagePath(x) {
      return new URL(`/src/assets/${x}.png`, import.meta.url).href;
    },
    addNlist(x) {
      if (this.nlist.length < 10) {
        this.nlist.push(x);
      }
    },
    reduceNlist() {
      this.nlist.pop();
    },
  },
  computed: {
    translated() {
      let numTranslated = [];
      for (let i = 2; i < 9; i++) {
        let word = this.nlist
          .map((x) => {
            if (x - i > 0) {
              return this.alphabets[x - i];
            } else {
              return this.alphabets[x - i + 25];
            }
          })
          .join("");
        numTranslated.push(word);
        fetch(`https://api.dictionaryapi.dev/api/v2/entries/en/${word}`).then(
          (response) => {
            if (response.status == 200) {
              this.nword[i - 2] = true;
            } else {
              this.nword[i - 2] = false;
            }
          }
        );
      }
      return numTranslated;
    },
  },
};
</script>

<style>
.shadow {
  box-shadow: 0 4px 4px 0 rgba(0, 0, 0, 0.5);
}
</style>
