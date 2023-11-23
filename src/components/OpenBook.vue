<script setup lang="ts">
import MagicCircle from "@/icons/MagicCircle.vue";
import { ref } from "vue";

const checkbox = ref();
const handleCheck = () => {
  setTimeout(() => {
    checkbox.value = false;
  }, 2000);
};
</script>

<template>
  <div class="container">
    <input
      v-model="checkbox"
      type="checkbox"
      id="checkbox"
      class=""
      @click="handleCheck"
    />
    <label for="checkbox" class="text-9xl">click me</label>
    <div class="mc-demo">
      <MagicCircle />
    </div>
    <div class="mc">
      <div class="translate-wrapper">
        <div class="spin-wrapper">
          <div class="scale-wrapper">
            <MagicCircle />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  @apply bg-grey-50 min-w-full;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
}

.mc-demo {
  @apply w-fit m-40 border-blue-500 border-2 border-solid p-5;
  > * {
    animation: demo-spin 2.5s linear infinite;
  }
}
.mc {
  position: absolute;
  right: 20%;
  bottom: 10%;
  scale: 25%;
}

@keyframes demo-spin {
  to {
    transform: rotate(360deg);
  }
}

@keyframes spin {
  30% {
    transform: rotate(1turn);
  }

  70% {
    transform: rotate(1turn);
  }

  90% {
    transform: rotate(2turn);
  }

  100% {
    transform: rotate(2turn);
  }
}

@keyframes translate {
  30% {
    transform: translateX(-30vw) translateY(-30vh);
  }

  70% {
    transform: translateX(-30vw) translateY(-30vh);
  }

  90% {
    transform: translateX(-100px) translateY(0px);
  }

  100% {
    transform: translateX(-100px) translateY(0px);
  }
}

@keyframes scale {
  0% {
    transform: scale(15%);
  }
  40% {
    transform: scale(150%);
  }
  70% {
    transform: scale(150%);
  }
  100% {
    transform: scale(15%);
  }
}
#checkbox:checked ~ .mc {
  scale: 1;
  .spin-wrapper {
    animation: spin 2s ease-in-out 1;
  }
  .translate-wrapper {
    animation: translate 2s ease-in-out 1;
  }
  .scale-wrapper {
    animation: scale 2s ease-in-out 1;
  }
}
</style>
