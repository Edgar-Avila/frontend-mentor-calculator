<script setup lang="ts">
import { ref } from 'vue';
let selectedTheme = ref(0);
let theme = {
  "theme-1": selectedTheme.value == 0,
  "theme-2": selectedTheme.value == 1,
  "theme-3": selectedTheme.value == 2,
}
let val = ref("");
let first = "";
let op = "";

function appendVal(event: Event) {
  const btn = event.target as HTMLButtonElement;
  val.value += btn.textContent || "";
}
function operation(event: Event) {
  const btn = event.target as HTMLButtonElement;
  op = btn.textContent || "";
  first = val.value || "0";
  val.value = "";
}
function calc() {
  if (first) {
    let ans = val.value;
    if (op == "+") ans = `${Number(first) + Number(val.value)}`;
    if (op == "-") ans = `${Number(first) - Number(val.value)}`;
    if (op == "x") ans = `${Number(first) * Number(val.value)}`;
    if (op == "/") ans = `${Number(first) / Number(val.value)}`;
    val.value = ans;
    first = val.value;
  }
  op = "";
}
function del() {
  if (val) val.value = val.value.slice(0, -1);
}
function reset() {
  val.value = "";
  first = "";
}
function toggle() {
  selectedTheme.value = ++selectedTheme.value % 3;
  theme = {
    "theme-1": selectedTheme.value == 0,
    "theme-2": selectedTheme.value == 1,
    "theme-3": selectedTheme.value == 2,
  }
}
</script>

<template>
  <div class="app" :class="theme">
    <div class="calculator">
      <div class="title">
        <span>calc</span>
        <div class="theme-picker">
          <span>theme</span>
          <div class="toggle-btn" @click="toggle" :class="{middle: selectedTheme == 1, right: selectedTheme == 2}">
            <span>1</span>
            <span>2</span>
            <span>3</span>
            <div class="toggle-btn-ball"></div>
          </div>
        </div>
      </div>
      <div class="display">
        {{ val || 0 }}
      </div>
      <div class="buttons">
        <div class="row">
          <button class="btn math" @click="appendVal">7</button>
          <button class="btn math" @click="appendVal">8</button>
          <button class="btn math" @click="appendVal">9</button>
          <button class="btn option" @click="del">DEL</button>
        </div>
        <div class="row">
          <button class="btn math" @click="appendVal">4</button>
          <button class="btn math" @click="appendVal">5</button>
          <button class="btn math" @click="appendVal">6</button>
          <button class="btn math" @click="operation">+</button>
        </div>
        <div class="row">
          <button class="btn math" @click="appendVal">1</button>
          <button class="btn math" @click="appendVal">2</button>
          <button class="btn math" @click="appendVal">3</button>
          <button class="btn math" @click="operation">-</button>
        </div>
        <div class="row">
          <button class="btn math" @click="appendVal">.</button>
          <button class="btn math" @click="appendVal">0</button>
          <button class="btn math" @click="operation">/</button>
          <button class="btn math" @click="operation">x</button>
        </div>
        <div class="row">
          <button class="btn option" @click="reset">RESET</button>
          <button class="btn equals" @click="calc">=</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.app {
  background-color: var(--bg-1);
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

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
  position: relative;
  display: flex;
  height: 16px;
  width: 45px;
  background-color: var(--bg-2);
  border-radius: 8px;
  padding: 2px;
  cursor: pointer;
}

.toggle-btn span {
  position: absolute;
  top: -15px;
}

.toggle-btn span:first-child {
  left: 0;
}

.toggle-btn span:nth-child(2) {
  left: 50%;
  transform: translateX(-50%);
}

.toggle-btn span:nth-child(3) {
  right: 0;
}

.toggle-btn-ball {
  background-color: var(--bg-5);
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
  box-shadow: inset 0px -3px 0px 0px var(--bg-4-dark);
  color: var(--fg-4);
}

.equals {
  background-color: var(--bg-5);
  box-shadow: inset 0px -3px 0px 0px var(--bg-5-dark);
  color: var(--fg-5);
}

.math {
  background-color: var(--bg-6);
  box-shadow: inset 0px -3px 0px 0px var(--bg-6-dark);
  color: var(--fg-6);
}

.middle {
  justify-content: center;
}

.right {
  justify-content: flex-end;
}
</style>
