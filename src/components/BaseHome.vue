<script setup lang="ts">
import HelloWorld from "@/components/HelloWorld.vue";
import Tag from "@/components/Tag.vue";
import Input from "@/components/Input.vue";
import { nextTick, ref } from "vue";

const inputVisible = ref(false);
const toggle = () => {
  inputVisible.value = !inputVisible.value;
};
const show = () => {
  toggle();
  nextTick(() => inputRef.value.$el.focus());
};
const inputRef = ref();
</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="@/assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <Input v-if="inputVisible" ref="inputRef" @toggle="toggle" />
  <Tag v-else @toggle="show" />
  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
