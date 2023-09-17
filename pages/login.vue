<template>
  <Head>
    <Title>DÖK Bejelentkezés</Title>
  </Head>
  <div>
    <div class="center-div">
      <UForm :validate="validate" :state="state" @submit="submit">
        <UFormGroup name="email">
          <UInput
            class="mb-3"
            placeholder="E-mail"
            type="email"
            v-model="state.email"
          />
        </UFormGroup>
        <UFormGroup name="password">
          <UInput
            class="mb-3"
            placeholder="Jelszo"
            v-model="state.password"
            type="password"
          />
        </UFormGroup>
        <UButton type="submit"> Bejelentkezés </UButton>
      </UForm>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import type { FormError, FormSubmitEvent } from "@nuxt/ui/dist/runtime/types";
const state = ref({
  email: undefined,
  password: undefined,
});
const validate = (state: any): FormError[] => {
  const errors = [];
  if (!state.email) errors.push({ path: "email", message: "Required" });
  if (!state.password) errors.push({ path: "password", message: "Required" });
  return errors;
};
async function submit(event: FormSubmitEvent<any>) {
  // Do something with data
  console.log(event.data);
}
</script>

<style scoped>
.center-div {
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  -ms-transform: translate(-50%, -80%); /* Not fully center since i think it's a bit weird. */
  transform: translate(-50%, -80%); /* Not fully center since i think it's a bit weird. */
}
</style>
