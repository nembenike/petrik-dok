<template>
    <div>
        <h2 class="text-4xl my-7">{{ event.title }}</h2>
        <p class="text-xl my-7">{{ event.description }}</p>
    </div>
</template>

<script setup>
    const { event } = defineProps(['event'])
</script>

<style lang="scss" scoped>

</style>