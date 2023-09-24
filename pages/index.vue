<template>
    <Head>
        <Title>DÖK App</Title>
    </Head>
    <div class="flex flex-col justify-center items-center">
        <h1 class="text-5xl">Petrik DÖK Webapp!</h1>
    </div>
</template>
  
<script setup>
/*in case we want to force the color scheme
definePageMeta({
  colorMode: 'dark',
}) */
definePageMeta({
    middleware: "auth"
})
</script>
  
<style scoped></style>
  