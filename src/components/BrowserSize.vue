<script setup>
import { onBeforeUnmount, onMounted, ref } from "vue";
const windowHeight = ref();
const windowWidth = ref();

onMounted(() => {
  window.addEventListener("resize", function () {
    windowHeight.value = window.innerHeight;
    windowWidth.value = window.innerWidth;
    console.log("hh");
  });
});

onBeforeUnmount(() => {
  window.removeEventListener;
});
</script>

<template>
  <div>
    <p>Window Height: {{ windowHeight }}</p>
    <p>Window Width: {{ windowWidth }}</p>
  </div>
</template>
