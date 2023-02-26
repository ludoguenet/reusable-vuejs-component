<template>
  <textarea
      :id="props.id"
      rows="4"
      :value="props.modelValue"
      v-on:input="$event => emit('update:modelValue', $event.target.value)"
      :class="[
         'block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500',
          props.validated ? 'border-green-300' : 'border-gray-300'
      ]"
  ></textarea>
</template>

<script setup lang="ts">
  const props = defineProps({
    id: String,
    modelValue: String,
    validated: Boolean,
  });

  const emit = defineEmits(['update:modelValue']);
</script>