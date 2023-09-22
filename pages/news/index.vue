<template>
    <Head>
        <title>
            Hírek
        </title>
    </Head>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-3">
        <newsCard />
        <newsCard />
        <newsCard />
        <newsCard />
        <newsCard />
        <newsCard />
    </div>
    <UPagination class="flex justify-center mt-3" size="xl" v-model="page" :page-count="5" :total="items.length" />
</template>

<script setup>
const page = ref(1)
const items = ref(Array(55))
</script>

<style lang="scss" scoped>

</style>