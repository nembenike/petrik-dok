<template>
    <div class="flex justify-center flex-col mt-7 mx-auto text-center w-100">
        <p class="mt-7 text-7xl font-bold">
            {{ error.statusCode }}
        </p>
        <p class="mt-7 text-6xl">
            Valami nem jó pali...
        </p>
        <img class="mt-8 w-80 self-center" src="https://media.discordapp.net/attachments/968844264471662613/1152904289941979146/280.jpg?width=674&height=676" />
        <p class="mt-7">{{ error.message }}</p>
        <UButton class="mt-4 self-center" size="xl" @click="handleClearError">Vissza a főoldalra...</UButton>
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