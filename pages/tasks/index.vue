<template>
    <Head>
        <Title>DÖK Feladatok</Title>
    </Head>
    <div>
        <h1 class="text-center text-4xl">This is where tasks will be listed</h1>
    </div>
</template>

<script setup>
    definePageMeta({
        middleware: ["auth"],
    });
</script>

<style lang="scss" scoped>

</style>