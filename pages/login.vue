<template>
  <Head>
    <Title>DÖK Bejelentkezés</Title>
  </Head>
  <div>
    <div class="center-div">
      <UForm :validate="validate" :state="state" @submit="submit">
        <UFormGroup name="username">
          <UInput
            class="mb-3"
            placeholder="Felhasználónév"
            type="username"
            v-model="state.username"
          />
        </UFormGroup>
        <UFormGroup name="password">
          <UInput
            class="mb-3"
            placeholder="Jelszó"
            v-model="state.password"
            type="password"
          />
        </UFormGroup>
        <UButton type="submit"> Bejelentkezés </UButton>
      </UForm>
      <a class="text-gray-500 hover:text-gray-600 text-sm" @click="isOpen = true">Regisztráció</a>
      <UModal v-model="isOpen">
        <h1 class="p-10 text-center">A regisztrácóhoz szólj valakinek. Mindenki manuálisan van hozzáadva az apphoz, a griefing elkerülése érdekében. Kapni fogsz egy felhasználónevet, és egy random generált jelszót amit majd megváltoztathatsz.</h1>
      </UModal>
    </div>
  </div>
</template>

<script setup lang="ts">
const isOpen = ref(false)
import { ref } from "vue";
import type { FormError, FormSubmitEvent } from "@nuxt/ui/dist/runtime/types";

const state = ref({
  username: undefined,
  password: undefined,
});

const validate = (state: any): FormError[] => {
  const errors = [];
  if (!state.username) errors.push({ path: "username", message: "Required" });
  if (!state.password) errors.push({ path: "password", message: "Required" });
  return errors;
};

async function submit(event: FormSubmitEvent<any>) {
  const postData = {
    username: state.value.username,
    password: state.value.password,
  };

  try {
    const response = await fetch("http://localhost/login", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(postData),
    });

    if (response.ok) {
      const data = await response.json();
      console.log("Login successful:", data);
    } else {
      console.error("Login failed:", response.statusText);
    }
  } catch (error) {
    console.error("An error occurred:", error);
  }
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
