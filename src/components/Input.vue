<template>
  <input
      :id="props.id"
      :value="props.modelValue"
      v-on:input="updateValue"
      :class="[
        'bg-gray-50 border text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500',
        props.validated ? 'border-green-300' : 'border-gray-300'
      ]"
  />
</template>

<script setup lang="ts">
 const props = defineProps({
   id: String,
   validated: Boolean,
   modelValue: String,
 });

 const emit = defineEmits(['update:modelValue']);
 const updateValue = (e: Event) => {
   emit('update:modelValue', (e.target as HTMLInputElement).value)
 };
</script>