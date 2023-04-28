<script setup>
import { ref } from 'vue';
import item from './components/item.vue';

const list = ref([])
const input = ref('')

function addItem() {
  list.value.push(input.value)
  clearField()
}

function removeItem(item) {
  const idx = list.value.indexOf(item)
  list.value.splice(idx, 1)
}

function clearField() {
  input.value = ''
}

</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <div class="wrapper">
    <div class="input-wrapper">
      <input v-model="input" type="text" class="input">
    </div>
    <button class="button" @click="addItem">
      Add item
    </button>
  </div>
  <div class="list-wrapper">
    <TransitionGroup name="slide">
      <item
        v-for="(item, index) in list"
        :key="index"
        :item="item"
        @remove-item="removeItem" />
    </TransitionGroup>
  </div>
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
.wrapper {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 12px;
}
.input-wrapper {
  border: 1px solid #41b883;
  border-radius: 4px;
  padding: 5px 10px;
  background-color: transparent;
}

.input {
  border: none;
  color: white;
  font-size: 16px;
  background-color: transparent;
}
.input:focus {
  outline: none
}

.button {
  width: fit-content;
  background-color: #41b883;
}
.button:active {
  border: none;
  outline: none;
}

.list-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 12px;
}

.slide-enter-from {
  opacity: 0;
  transform: translate(15px);
}
.slide-enter-to {
  opacity: 1;
  transform: translate(0px);
}
.slide-enter-active {
  transition: all 500ms ease-in;
}
.slide-leave-from {
  opacity: 1;
  transform: translate(0px);
}
.slide-leave-to {
  opacity: 0;
  transform: translate(-15px);
}
.slide-leave-active {
  transition: all 500ms ease-in;
}
</style>
