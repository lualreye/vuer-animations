<script setup>
const emit = defineEmits(['remmove-item'])

const props = defineProps({
  item: {
    type: String,
    required: true
  }
})

function removeItem(item) {
  emit('remove-item', item)
}

</script>

<template>
  <div v-if="item.length" class="item-wrapper">
    <p class="item">
      {{ item }}
    </p>
    <button class="button" @click="removeItem(item)">
      Borrar
    </button>
  </div>
</template>

<style scoped>
.item-wrapper {
  width: 100%;
  margin-bottom: 8px;
  padding: 2px 12px;
  border-radius: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #ab4bff;
}

.item {
  color: white;
  font-size: 16px;
}

.button {
  background: #ed7777;
  font-size: 12px;
}
</style>
