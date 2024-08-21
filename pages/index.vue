<template>
  <UContainer class=" items-center h-screen justify-center flex bg-slate-50">
    <div class="content">
      <h1 class="title">Choose White or Black</h1>
      <div class="buttons">
        <UButton color="white" variant="solid" @click="choose('white')" class="button">White</UButton>
        <UButton color="black" variant="solid" @click="choose('black')" class="button">Black</UButton>
      </div>
      <p v-if="result" class="result">{{ result }}</p>
      <p class="text-red-600">Score: {{ score }}</p>
    </div>
  </UContainer>
</template>

<script setup>
import { ref } from 'vue'

const result = ref('')
const score = ref(0)

function choose(playerChoice) {
  const colors = ['white', 'black']
  const computerChoice = colors[Math.floor(Math.random() * colors.length)]

  if (playerChoice === computerChoice) {
    result.value = `You chose ${playerChoice}. The computer chose ${computerChoice}. You won!`
    score.value += 1
  } else {
    result.value = `You chose ${playerChoice}. The computer chose ${computerChoice}. You lost.`
    score.value -= 1
  }
}
</script>

<style scoped>

.content {
  text-align: center;
  background: white;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.title {
  margin-bottom: 1rem;
  font-size: 2rem;
  color: #333;
}

.buttons {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 1rem;
}

.button {
  font-size: 1.1rem;
  padding: 0.75rem 1.5rem;
}

.result {
  font-size: 1.2rem;
  color: #333;
  margin-bottom: 1rem;
}

.score {
  font-size: 1.5rem;
  font-weight: bold;
  color: #007bff;
}
</style>
