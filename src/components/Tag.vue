<script setup lang="ts">
</script>

<template>
  <div class="tag" @click="$emit('toggle')">tag</div>
</template>

<style scoped>
.tag {
  background-color: bisque;
  border: 2px black solid;
}
</style>
