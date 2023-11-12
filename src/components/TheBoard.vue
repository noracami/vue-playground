<script setup lang="ts">
const NUM = 11;
const board = [...Array(NUM)].map((_, row) => {
  return [...Array(NUM)].map((_, cell) => {
    return `${String.fromCharCode(65 + row - 1)},${NUM - cell - 1}`;
  });
});
</script>

<template>
  <div class="board">
    <div class="row" v-for="row of board">
      <div v-for="cell of row" class="cell">
        <span :data-col="cell[0]" :data-row="cell.split(',')[1]"></span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.board {
  display: grid;
  grid-template-columns: repeat(11, minmax(0, 1fr));

  .row:nth-child(10n + 1) > :nth-child(10n + 1) {
    background-color: var(--background-color, black);

    ::after {
      display: none;
    }
  }

  .row:nth-child(10n + 1) {
    &:hover {
      animation-play-state: paused;
    }

    ::after {
      content: attr(data-row);
      font-size: 2rem;
    }
  }

  .cell:nth-child(10n + 1) {
    ::after {
      content: attr(data-col);
      font-size: 2rem;
    }
  }

  .cell {
    display: flex;
    justify-content: center;
    align-items: center;

    width: 70px;
    aspect-ratio: 1/1;

    border: solid black 1px;
    background-color: var(--board-background-color, black);

    &:hover {
      animation: breathing-light 0.7s infinite;
      border-color: white;
    }
  }
}

@keyframes breathing-light {
  0% {
    outline: 3px solid blue;
    scale: 95%;
  }

  10% {
    outline: 4px solid blue;
  }

  100% {
    outline: 5px solid blue;
    scale: 100%;
  }
}
</style>
