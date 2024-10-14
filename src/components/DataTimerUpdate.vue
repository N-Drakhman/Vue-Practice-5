<script setup>
import {
  onActivated,
  onBeforeMount,
  onBeforeUnmount,
  onDeactivated,
  onMounted,
  onUnmounted,
  ref,
} from "vue";
import axios from "axios";

const jobs = ref([]);

let intervalId;

async function ipdateOIntervalId() {
  if (!intervalId) {
    intervalId = setInterval(async () => {
      try {
        const response = await axios.get("http://localhost:5000/jobs/");
        jobs.value = response.data;
      } catch {
        console.error("Error Loading data", error);
      }

      console.log("updated");
    }, "1000");
  }
}

onBeforeMount(() => ipdateOIntervalId());

onDeactivated(() => {
  clearInterval(intervalId);
  intervalId = null;
});

onActivated(() => ipdateOIntervalId());
</script>

<template>
  <ul>
    <li v-for="job in jobs">{{ job.description }}</li>
  </ul>
</template>
