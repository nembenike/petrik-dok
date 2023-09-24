<template>
    <div>
        <Head>
            <Title>DÖK Események | {{ event.title }}</Title>
        </Head>
        <EventDetails :event="event" />
    </div>
</template>

<script setup>
    const { id } = useRoute().params
    const uri = `https://fakestoreapi.com/products/` + id

    const { data: event } = await useFetch(uri, { key: id })
    definePageMeta({
        middleware: ["auth"],
    });
</script>

<style lang="scss" scoped>

</style>