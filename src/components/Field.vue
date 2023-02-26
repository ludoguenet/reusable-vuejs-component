<template>
  <Label
      :for="props.id"
  >
    {{ props.labelName }}
  </Label>

  <slot
      v-bind="props"
  />
</template>

<script setup lang="ts">
import Label from "@/components/Label.vue";

const props = defineProps({
  id: String,
  labelName: String,
});
</script>
