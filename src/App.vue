<template>
  <div class="container mx-auto px-4 mt-10">
    <form
      v-on:submit.prevent="submit"
    >
      <div class="grid gap-6 mb-6 md:grid-cols-2">

        <div>

          <Field
            id="first_name"
            label-name="First name"
            v-slot="slotProps"
          >

            <Input
                v-bind="slotProps"
                v-model="form.firstName"
                :validated="validated.firstName"
                required
                type="text"
                placeholder="My First Name"
            />

          </Field>

        </div>

        <div>

          <Field
              id="email"
              label-name="Email"
              v-slot="slotProps"
          >

            <Input
                v-bind="slotProps"
                v-model="form.email"
                :validated="validated.email"
                required
                type="text"
                placeholder="My First Name"
            />

          </Field>

        </div>

        <div>

          <Field
              id="password"
              label-name="Password"
              v-slot="slotProps"
          >

            <Input
                v-bind="slotProps"
                v-model="form.password"
                :validated="validated.password"
                required
                type="password"
            />

          </Field>

        </div>

        <div>

          <Field
              id="description"
              label-name="Description"
              v-slot="slotProps"
          >

            <TextArea
                v-bind="slotProps"
                v-model="form.description"
                :validated="validated.description"
                required
            />

          </Field>

        </div>

      </div>

      <button type="submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Submit</button>

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
    password: '',
    description: '',
  });

  const validated: Validated = reactive({
    firstName: false,
    email: false,
    password: false,
    description: false,
  });

  const submit = (): void => {
    validated.firstName = true;
    validated.email = true;
    validated.password = true;
    validated.description = true;

    console.log(form);
  }
</script>