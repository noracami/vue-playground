<script setup lang="ts">
import { computed, ref } from "vue";
const degree = ref(0);
const cssPropsBox = computed(() => {
  return {
    "--rotate-degree": `-${degree.value}deg`,
  };
});
const cssPropsElement = computed(() => {
  return {
    "--rotate-degree": `${degree.value}deg`,
  };
});
</script>

<template>
  <div class="container">
    <div class="box" :style="cssPropsBox">
      <div v-for="i of 5" :key="i" class="element" :style="cssPropsElement">
        <p class="player">player {{ i }}</p>
        <p class="player-info" :data-count="i">{{ i }}</p>
      </div>
    </div>
    <input type="range" max="360" class="range" v-model="degree" />
    <p class="degree">{{ degree }}</p>
  </div>
</template>

<style scoped>
.box > :nth-child(1) {
  --nth-child: 1;
}
.box > :nth-child(2) {
  --nth-child: 2;
}
.box > :nth-child(3) {
  --nth-child: 3;
}
.box > :nth-child(4) {
  --nth-child: 4;
}
.box > :nth-child(5) {
  --nth-child: 5;
}
.container,
.box,
.element {
  aspect-ratio: 1;
}
.container {
  --box-width: 100px;

  position: relative;
  width: calc(5 * var(--box-width));
  outline: 5px blue solid;
}
.box {
  position: absolute;
  margin: auto;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  height: var(--box-width);
  animation: spin-left 10s linear infinite;
  rotate: var(--rotate-degree);
}
.element {
  --radius: var(--box-width);
  --deg: calc(360deg / 5);

  position: absolute;
  width: 100%;
  border-radius: 9999px;
  background-color: #ffa;
  color: black;
  display: flex;
  justify-content: center;
  align-items: center;
  left: calc(var(--radius) * sin(var(--nth-child) * var(--deg)));
  top: calc(var(--radius) * cos(var(--nth-child) * var(--deg)));
}
.player {
  position: relative;
  display: flex;
  rotate: var(--rotate-degree);
  animation: spin-right 10s linear infinite;
}
.player-info {
  --radius: calc(var(--box-width) * -0.65);

  position: absolute;
  color: blue;
  width: 25px;
  height: 25px;
  border-radius: 9999px;
  display: inline-block;
  text-align: center;
  background-color: #fff;
  outline: 1px red solid;
  rotate: var(--rotate-degree);
  animation: spin-right 10s linear infinite;
  translate: calc(var(--radius) * sin(calc(18deg + var(--nth-child) * 72deg)))
    calc(var(--radius) * cos(calc(18deg + var(--nth-child) * 72deg)));
}

.degree {
  color: white;
}
.range {
  width: 100%;
}

/* ---------- Animation ---------- */
@keyframes spin-right {
  100% {
    -webkit-transform: rotate(360deg);
    -moz-transform: rotate(360deg);
    -ms-transform: rotate(360deg);
    -o-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
@keyframes spin-left {
  100% {
    -webkit-transform: rotate(-360deg);
    -moz-transform: rotate(-360deg);
    -ms-transform: rotate(-360deg);
    -o-transform: rotate(-360deg);
    transform: rotate(-360deg);
  }
}
</style>
