<script setup lang="ts">
import { ref } from 'vue';
import BaseHome from './components/BaseHome.vue';
import TheBoard from './components/TheBoard.vue';

const currentTab = ref('BaseHome')

interface Tabs<T> {
  [key: string]: T
}

const tabs: Tabs<unknown> = {
  BaseHome,
  TheBoard
}

</script>

<template>
  <div class="demo">
    <button v-for="(_, tab) in tabs" :key="tab" :class="['tab-button', { active: currentTab === tab }]"
      @click="currentTab = String(tab)">
      {{ tab }}
    </button>
  </div>
  <component :is="tabs[currentTab]" class="tab"></component>
</template>

<style scoped>
.demo {
  position: absolute;
  left: 10px;
  top: 10px;

  .tab-button {
    margin: 2px;
  }
}
</style>
