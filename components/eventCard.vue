<template>
    <div>
        <p>{{ event.title }}</p>
        <NuxtLink :to="`/events/${event.id}`">Visit event</NuxtLink>
    </div>
</template>

<script setup>
        const { event } = defineProps(['event'])
</script>

<style lang="scss" scoped>

</style>