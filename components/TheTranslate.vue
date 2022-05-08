<template>
  <div class="translate">
    <div class="block-language d-flex justify-content-between">
      <div class="block-language__text d-flex">
        <p class="language-text">Из</p>
        <TheOption @newLanguageCheked="newLanguageOneUpdate" />
      </div>
      <div class="block-language__text d-flex">
        <p class="language-text">В</p>
        <TheOption @newLanguageCheked="newLanguageTwoUpdate" />
      </div>
    </div>
    <div class="block-translate d-flex justify-content-between mt-2">
      <div class="block-translate-child">
        <TheAreaTranslate @create="translate" />
      </div>
      <div class="block-translate-child" @click="addText">
        <p class="translate-text">{{ readyText }}</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      textTranslate: "",
      newLanguageOne: "",
      newLanguageTwo: "",
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
        headers: {
          "content-type": "application/json",
          "X-RapidAPI-Host": "deep-translate1.p.rapidapi.com",
          "X-RapidAPI-Key":
            "76d7e06148msh263d850659d08bdp1c483cjsnf26e619a4a8c",
        },
        body: `{"q":"${this.textTranslate}","source":"${this.newLanguageOne}","target":"${this.newLanguageTwo}"}`,
      };

      fetch(
        "https://deep-translate1.p.rapidapi.com/language/translate/v2",
        options
      )
        .then((response) => response.json())
        .then((response) => {
          this.readyText = response.data.translations.translatedText;
        })
        .catch((err) => console.error(err));
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