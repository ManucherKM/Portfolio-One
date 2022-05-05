<template>
  <div class="translate">
    <div class="block-translate d-flex">
      <div class="block-translate-child">
        <TheAreaTranslate />
      </div>
      <div class="block-translate-child">1</div>
    </div>
  </div>
</template>

<script>
import TheAreaTranslate from "./TheAreaTranslate.vue";
export default {
  components: { TheAreaTranslate },
};
</script>

<style>
</style>