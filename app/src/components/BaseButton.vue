<script setup lang="ts">
import { computed, toRefs } from 'vue'

interface Props {
  label: string
  primary: boolean
  disabled?: boolean
}

const props = defineProps<Props>()
const { label, primary, disabled } = toRefs(props)

const classObject = computed(() => {
  return {
    'button--primary': primary.value,
    'button--contained': !primary.value && !disabled?.value,
    'button--disabled': !primary.value && disabled?.value,
  }
})
</script>

<template>
  <button :class="['button', classObject]" type="button" :disabled="disabled">
    {{ label }}
  </button>
</template>

<style scoped>
.button {
  min-width: 100px;
  height: 40px;
  padding: 0;
  border: 0;
  border-radius: 6px;
  font-size: 14px;
  text-transform: uppercase;
  cursor: pointer;
}

.button--primary {
  background-color: #8fc9f9;
}

.button--primary:hover {
  background-color: #42a5f5;
}

.button--contained {
  background-color: #0a1929;
  color: #8fc9f9;
}

.button--contained:hover {
  background-color: #152839;
}

.button--disabled:disabled {
  cursor: default;
  background-color: #0a1929;
  color: #505a65;
}
</style>
