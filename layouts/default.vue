<template>
    <div>
        <nav class="bg-green-500 flex justify-between items-center">
            <ul>
                <li class="ml-2"><UButton size="xl" to="/">DÖK</UButton></li>
            </ul>
            <ul class="flex flex-direction-row pt-3 pb-3">
                <li class="mr-2"><UButton to="/events" size="xl">Események</UButton></li>
                <li class="mr-2"><UButton to="/tasks" size="xl">Feladataid</UButton></li>
                <li class="mr-2"><UAvatar size="md" src="https://avatars.githubusercontent.com/u/739984?v=4" alt="Avatar" /></li>
            </ul>
        </nav>
        <slot />
    </div>
</template>

<script setup>

</script>

<style scoped>

</style>