<script setup>
import { ref } from "vue";
import BrowserSize from "./components/BrowserSize.vue";
import DataTimerUpdate from "./components/DataTimerUpdate.vue";

const render1 = ref(true);
const render2 = ref(true);
</script>

<template>
  <div class="block">
    <div class="task1">
      <button @click="render1 = !render1">Show Resize</button>
      <BrowserSize v-if="render1"></BrowserSize>
    </div>

    <div class="task2">
      <button @click="render2 = !render2">On/Off</button>
      <KeepAlive>
        <DataTimerUpdate v-if="render2"></DataTimerUpdate>
      </KeepAlive>
    </div>
  </div>
</template>

<style scoped>
.block {
  display: flex;
  gap: 150px;
  position: absolute;
  top: 0;
  left: 0;
}

button {
  width: 150px;
  height: 50px;
}

.task2 {
  width: 500px;
}
</style>
