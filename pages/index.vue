<template>
    <Head>
        <Title>DÖK App</Title>
    </Head>
    <div class="flex flex-col justify-center items-center">
        <h1 class="text-5xl">Petrik DÖK Webapp!</h1>
        <div class="flex flex-col items-center mt-4">
            <UButton to="/login" size="xl">Belépés</UButton>
        </div>
    </div>
</template>
  
<script setup>
/*in case we want to force the color scheme
definePageMeta({
  colorMode: 'dark',
}) */
</script>
  
<style scoped></style>
  