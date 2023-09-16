<template>
        <nav class="bg-green-500 flex justify-between items-center">
            <ul>
                <li class="ml-2">
                    <UButton size="xl" to="/">DÖK</UButton>
                </li>
            </ul>
            <ul class="flex flex-direction-row pt-3 pb-3">
                <li class="mr-2">
                    <UButton to="/admin/" size="xl">Admin</UButton>
                </li>
                <li class="mr-2">
                    <UButton to="/events/" size="xl">Események</UButton>
                </li>
                <li class="mr-2">
                    <UButton to="/tasks" size="xl">Feladataid</UButton>
                </li>
                <li class="mr-2">
                    <UDropdown :items="items" :ui="{ item: { disabled: 'cursor-text select-text' } }"
                        :popper="{ placement: 'bottom-start' }">
                        <UAvatar size="md" src="https://avatars.githubusercontent.com/u/739984?v=4" />
                        <template #account="{ item }">
                            <div class="text-left">
                                <p>
                                    Signed in as
                                </p>
                                <p class="truncate font-medium text-gray-900 dark:text-white">
                                    {{ item.label }}
                                </p>
                            </div>
                        </template>
                        <template #item="{ item }">
                            <span class="truncate">{{ item.label }}</span>
                            <UIcon :name="item.icon"
                                class="flex-shrink-0 h-4 w-4 text-gray-400 dark:text-gray-500 ms-auto" />
                        </template>
                    </UDropdown>
                </li>
            </ul>
        </nav>
</template>

<script setup>
const items = [
    [{
        label: 'ben@example.com',
        slot: 'account',
        disabled: true
    }], [{
        label: 'Settings',
        icon: 'i-heroicons-cog-8-tooth'
    }], [{
        label: 'Documentation',
        icon: 'i-heroicons-book-open'
    }, {
        label: 'Changelog',
        icon: 'i-heroicons-megaphone'
    }, {
        label: 'Status',
        icon: 'i-heroicons-signal'
    }], [{
        label: 'Sign out',
        icon: 'i-heroicons-arrow-left-on-rectangle'
    }]
]
</script>