<script setup lang="ts"></script>

<template>
  <input value="input" class="tag" @blur="$emit('toggle')" />
</template>

<style scoped>
.tag {
  background-color: whitesmoke;
  border: 2px black solid;
  padding: 10px;
}

.tag:focus {
  border: 4px red solid;
}
</style>
