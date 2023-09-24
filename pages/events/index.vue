<template>
    <Head>
        <Title>DÖK Események</Title>
    </Head>
    <div>
        <h1 class="text-4xl text-center mb-10 mt-5">Events</h1>
    </div>
    <div class="grid grid-cols-4 gap-5 mr-5 ml-5">
        <div v-for="e in events">
            <EventCard :event="e" />
        </div>
    </div>
</template>

<script setup>
    const { data: events } = await useFetch('https://fakestoreapi.com/products')
    definePageMeta({
        middleware: ["auth"],
    });
</script>

<style lang="scss" scoped>

</style>