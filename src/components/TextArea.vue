<template>
  <textarea
      :id="props.id"
      :value="props.modelValue"
      rows="4"
      v-on:input="updateValue"
      :class="[
        'block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500',
        props.validated ? 'border-green-300' : 'border-gray-300'
      ]"
  ></textarea>
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