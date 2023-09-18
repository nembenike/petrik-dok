<template>
    <div class="mt-7 max-w-sm mx-auto text-center card">
        <p class="mt-7 text-7xl font-bold">
            {{ error.statusCode }}
        </p>
        <p class="mt-7 text-6xl">
            Valami nem jó pali...
        </p>
        <p class="mt-7">{{ error.message }}</p>
        <UButton class="mt-4" size="xl" @click="handleClearError">Vissza a főoldalra...</UButton>
    </div>
</template>

<script setup>
    defineProps(['error'])

    const handleClearError = () => {
        clearError({ redirect: '/' })
    }
</script>

<style scoped>

</style>