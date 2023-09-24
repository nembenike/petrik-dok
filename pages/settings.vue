<template>
    <div>
        <h1 class="text-center text-2xl">Beállítások</h1>
        <p>Email: {{ user.email }}</p>
    </div>
</template>

<script setup>
    useHead({  title: 'Beállítások'})
    definePageMeta({
        middleware: ["auth"],
    });
    const user = useSupabaseUser();
</script>

<style lang="scss" scoped>

</style>