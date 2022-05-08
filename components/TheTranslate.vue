<template>
  <div class="translate">
    <form class="block-language d-flex justify-content-center">
      <div class="block-language__text d-flex mr-20">
        <p class="language-text">From</p>
        <TheOption @newLanguageCheked="newLanguageOneUpdate" />
      </div>
      <div class="block-language__text d-flex mr-20 mt-phone">
        <p class="language-text text-w">To</p>
        <TheOption @newLanguageCheked="newLanguageTwoUpdate" />
      </div>
      <button type="button" class="btn btn-outline-success mt-phone" @click="addText">
        Run
      </button>
    </form>
    <div class="block-translate d-flex justify-content-between mt-2">
      <div class="block-translate-child">
        <TheAreaTranslate @create="translate" />
      </div>
      <div class="block-translate-child">
        <p class="translate-text">{{ readyText }}</p>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      textTranslate: "",
      newLanguageOne: "en",
      newLanguageTwo: "ru",
      readyText: "",
    };
  },
  methods: {
    translate(text) {
      this.textTranslate = text;
    },
    addText() {
      const options = {
        method: "POST",
        url: "https://deep-translate1.p.rapidapi.com/language/translate/v2",
        headers: {
          "content-type": "application/json",
          "X-RapidAPI-Host": "deep-translate1.p.rapidapi.com",
          "X-RapidAPI-Key":
            "76d7e06148msh263d850659d08bdp1c483cjsnf26e619a4a8c",
        },
        data: `{"q":"${this.textTranslate.replace(/\s{2,}/g, " ")}","source":"${
          this.newLanguageOne
        }","target":"${this.newLanguageTwo}"}`,
      };
      axios
        .request(options)
        .then((response) => {
          this.readyText = response.data.data.translations.translatedText;
          console.log(response.data.data.translations.translatedText);
        })
        .catch(function (error) {
          console.error(error);
        });
    },
    newLanguageOneUpdate(newwVal) {
      this.newLanguageOne = newwVal;
    },
    newLanguageTwoUpdate(newwVal) {
      this.newLanguageTwo = newwVal;
    },
  },
};
</script>

<style>
</style>