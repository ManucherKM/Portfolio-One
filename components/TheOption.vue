<template>
    <select class="form-select" aria-label="Default select example" v-model.lazy="nameLanguage">
      <option :value="option.language" v-for="option in mass" :key="option.language">
        {{ option.name }}
      </option>
    </select>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      mass: [],
      nameLanguage: "",
    };
  },
  // methods: {
  //   log() {
  //     console.log(this.nameLanguage);
  //   },
  // },
  beforeMount() {
    const options = {
      method: "GET",
      url: "https://deep-translate1.p.rapidapi.com/language/translate/v2/languages",
      headers: {
        "X-RapidAPI-Host": "deep-translate1.p.rapidapi.com",
        "X-RapidAPI-Key": "76d7e06148msh263d850659d08bdp1c483cjsnf26e619a4a8c",
      },
    };

    axios
      .request(options)
      .then((response) => {
        this.mass = response.data.languages;
      })
      .catch(function (error) {
        console.error(error);
      });
  },
  watch: {
    nameLanguage(newQuestion) {
      this.$emit("newLanguageCheked", this.nameLanguage);
    },
  },
};
</script>

<style>
</style>