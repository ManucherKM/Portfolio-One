<template>
  <select class="select" v-model="nameLanguage">
    <option
      :value="option.language"
      v-for="option in mass"
      :key="option.language"
    >
      {{ option.name }}
    </option>
  </select>
</template>

<script>
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
    try {
      const options = {
        method: "GET",
        headers: {
          "X-RapidAPI-Host": "deep-translate1.p.rapidapi.com",
          "X-RapidAPI-Key":
            "76d7e06148msh263d850659d08bdp1c483cjsnf26e619a4a8c",
        },
      };

      fetch(
        "https://deep-translate1.p.rapidapi.com/language/translate/v2/languages",
        options
      )
        .then((response) => response.json())
        .then((response) => {
          this.mass = response.languages;
        })
        .catch((err) => console.error(err));
    } catch (error) {
      console.log(error);
    }
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