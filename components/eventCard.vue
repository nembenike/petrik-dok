<template>
    <div>
        <UCard>
            <template #header>
                <p>{{ event.title }}</p>
            </template>
            <p class="truncate">{{ event.description }}</p>
            <template #footer>
                <UButton :to="`/events/${event.id}`">Megnézem</UButton>
            </template>
        </UCard>
    </div>
</template>

<script setup>
        const { event } = defineProps(['event'])
</script>

<style lang="scss" scoped>

</style>