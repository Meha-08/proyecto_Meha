<script setup>
import { ref, watch } from 'vue';

const props = defineProps(['label', 'type', 'placeholder', 'modelValue']);
const inputValue = ref(props.modelValue);

watch(() => props.modelValue, (val) => {
  inputValue.value = val;
});
</script>

<template>
  <div>
    <label>{{ label }}</label>
    <input
      :type="type"
      :placeholder="placeholder"
      v-model="inputValue"
      @input="$emit('update:modelValue', inputValue)"
    />
  </div>
</template>
