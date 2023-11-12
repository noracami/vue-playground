<script setup lang="ts">
import { ref } from "vue";
import BaseHome from "./components/BaseHome.vue";
import TheBoard from "./components/TheBoard.vue";
import CircularDistribution from "./components/CircularDistribution.vue";

const currentTab = ref("2. Circular Distribution Items");

interface Tabs<T> {
  [key: string]: T;
}

const tabs: Tabs<unknown> = {
  "0. BaseHome": BaseHome,
  "1. TheBoard": TheBoard,
  "2. Circular Distribution Items": CircularDistribution,
};
</script>

<template>
  <div class="demo">
    <button
      v-for="(_, tab) in tabs"
      :key="tab"
      :class="['tab-button', { active: currentTab === tab }]"
      @click="currentTab = String(tab)"
    >
      {{ tab }}
    </button>
  </div>
  <component :is="tabs[currentTab]"></component>
</template>

<style scoped>
.demo {
  position: absolute;
  left: 10px;
  top: 10px;
  display: flex;
  flex-direction: column;
  gap: 5px;
  > .tab-button {
    text-align: start;
  }
  > .active {
    background: #00f;
  }
}
</style>
