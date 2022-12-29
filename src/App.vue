<script setup lang="ts">
const val = 0;
</script>

<template>
  <div class="calculator">
    <div class="title">
      <span>calc</span>
      <div class="theme-picker">
        <span>theme</span>
        <div class="toggle-btn">
          <div class="toggle-btn-ball"></div>
        </div>
      </div>
    </div>
    <div class="display">
      {{ val }}
    </div>
    <div class="buttons">
      <div class="row">
        <button class="btn math seven">7</button>
        <button class="btn math eight">8</button>
        <button class="btn math nine">9</button>
        <button class="btn option">DEL</button>
      </div>
      <div class="row">
        <button class="btn math four">4</button>
        <button class="btn math five">5</button>
        <button class="btn math six">6</button>
        <button class="btn math plus">+</button>
      </div>
      <div class="row">
        <button class="btn math one">1</button>
        <button class="btn math two">2</button>
        <button class="btn math three">3</button>
        <button class="btn math minus">-</button>
      </div>
      <div class="row">
        <button class="btn math point">.</button>
        <button class="btn math zero">0</button>
        <button class="btn math divided-by">/</button>
        <button class="btn math times">x</button>
      </div>
      <div class="row">
        <button class="btn option">RESET</button>
        <button class="btn equals">=</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.calculator {
  margin: auto;
  max-width: 300px;
  display: flex;
  flex-direction: column;
  gap: 1em;
  flex-grow: 1;
}

.title {
  display: flex;
  justify-content: space-between;
  color: var(--fg-1);
}

.theme-picker {
  display: flex;
  gap: 0.5em;
}

.toggle-btn {
  height: 16px;
  width: 45px;
  background-color: var(--bg-2);
  border-radius: 8px;
  padding: 2px;
}

.toggle-btn-ball {
  background-color: orange;
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.display {
  padding: 0.5em;
  background-color: var(--bg-3);
  color: var(--fg-3);
  border-radius: 5px;
  text-align: right;
  font-size: xx-large;
}

.buttons {
  padding: 1em;
  background-color: var(--bg-2);
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  gap: 1em;
}

.row {
  display: flex;
  gap: 1em;
}

.btn {
  flex-grow: 1;
  flex-basis: 0;
  padding: 0.5em 0;
  font-size: larger;
  border: none;
  border-radius: 5px;
}

.option {
  background-color: var(--bg-4);
  color: var(--fg-4);
}

.equals {
  background-color: var(--bg-5);
  color: var(--fg-5);
}

.math {
  background-color: var(--bg-6);
  color: var(--fg-6);
}
</style>
