<template>
  <textarea placeholder="Enter text" v-model="areaOneText" @input="run" cols="30" rows="10"></textarea>
</template>

<script>
export default {
  data() {
    return {
      areaOneText: "",
    };
  },
  methods: {
    run() {
      this.$emit("create", this.areaOneText);
    },
  },
};
</script>

<style>
</style>