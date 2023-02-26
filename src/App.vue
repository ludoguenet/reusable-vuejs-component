<template>
  <div class="container mx-auto px-4 mt-10">
    <form
      v-on:submit.prevent="submit"
    >
      <div class="grid gap-6 mb-6 md:grid-cols-2">

        <div>

          <Field
              id="first_name"
              label-name="First Name"
              v-slot="slotProps"
          >
            <Input
                v-if="form.firstName !== null"
                :id="slotProps.id"
                :validated="validated.firstName"
                v-model="form.firstName"
                type="text"
                placeholder="John"
                required
            />
          </Field>

        </div>

        <div>

          <Field
              id="email"
              label-name="My Email"
              v-slot="slotProps"
          >
            <Input
                v-if="form.email !== null"
                :id="slotProps.id"
                :validated="validated.email"
                v-model="form.email"
                type="email"
                placeholder="email@test.com"
                required
            />
          </Field>

        </div>

        <div>

          <Field
              id="description"
              label-name="My Description"
              v-slot="slotProps"
          >
            <TextArea
                v-if="form.description !== null"
                :id="slotProps.id"
                :validated="validated.description"
                v-model="form.description"
                required
            />
          </Field>

        </div>

      </div>

      <button
          type="submit"
          class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
      >
        Submit
      </button>

    </form>

  </div>
</template>

<script setup lang="ts">
  import { reactive } from "vue";
  import type { Validated } from "@/types/Validated";
  import type { Form } from "@/types/Form";
  import Input from "@/components/Input.vue";
  import Field from "@/components/Field.vue";
  import TextArea from "@/components/TextArea.vue";

  const form: Form = reactive({
    firstName: '',
    email: '',
    description: '',
  });

  const validated: Validated = reactive({
    firstName: false,
    email: false,
    description: false,
  });

  const submit = (): void => {
    validated.firstName = true;
    validated.email = true;
    validated.description = true;

    console.log(form);
  }
</script>