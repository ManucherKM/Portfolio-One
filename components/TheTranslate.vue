<template>
  <div class="translate">
    <div class="block-translate d-flex">
      <TheOption />
      <div class="block-translate-child">
        <TheAreaTranslate @create="translate" />
      </div>
      <div class="block-translate-child">
        <p class="translate-text">1</p>
      </div>
    </div>
  </div>
</template>
<script>
import TheOption from "./TheOption.vue";
export default {
  data() {
    return {
      textTranslate: ""
    };
  },
  methods: {
    translate(text) {
      console.log(text); //Текст компонента
    },
    runApi() {
      const options = {
        method: "POST",
        headers: {
          "X-RapidAPI-Host": "deep-translate1.p.rapidapi.com",
          "X-RapidAPI-Key": "76d7e06148msh263d850659d08bdp1c483cjsnf26e619a4a8c"
        }
      };
      fetch("https://deep-translate1.p.rapidapi.com/language/translate/v2/detect", options)
        .then(response => response.json())
        .then(response => console.log(response))
        .catch(err => console.error(err));
    }
  },
  components: { TheOption }
}

</script>

<style>
</style>