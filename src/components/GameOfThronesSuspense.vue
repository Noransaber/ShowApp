<script setup>
import GameOfThronesCards from './GameOfThronesCards.vue'

</script>

<template>
    <Suspense>
      <template #fallback>
        <div class="card spinner">
          <n-spin size="large" />
        </div>
      </template>

      <template #default>
        <GameOfThronesCards />
      </template>
    </Suspense>
</template>

<style scoped>
.card{
  height: 700px;
  background-color: rgb(27, 26, 26);
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>