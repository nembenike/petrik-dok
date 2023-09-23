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
        <UButton type="submit" :disabled="!isLoginFormValid"> Bejelentkezés </UButton>
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
  if (!state.username) errors.push({ path: "username", message: " " });
  if (!state.password) errors.push({ path: "password", message: " " });
  return errors;
};

async function submit(event: FormSubmitEvent<any>) {
  const postData = {
    username: state.value.username,
    password: state.value.password,
  };

  try {
    const response = await fetch("http://localhost:8080/login", {
      method: "POST",
      credentials: 'include',
      headers: {
        "Content-Type": "application/json",
        "Credentials": 'include',
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
import { computed } from "vue";

const isLoginFormValid = computed(() => {
  return !!(state.value.username && state.value.password);
});
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
