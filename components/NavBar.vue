<template>
        <nav class="bg-green-500 flex justify-between items-center">
            <ul>
                <li class="ml-2">
                    <UButton size="xl" to="/">DÖK</UButton>
                </li>
            </ul>
            <ul class="flex flex-direction-row pt-3 pb-3">
                <li class="mr-2">
                    <UButton to="/news/" size="xl">Hírek</UButton>
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
                                    Bejelentkezve
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
        label: 'sussy.mihály',
        slot: 'account',
        disabled: true
    }], [{
        label: 'Beállítások',
        icon: 'i-heroicons-cog-8-tooth',
        to: '/settings'
    }], [{
        label: 'Feladataid',
        icon: 'i-heroicons-book-open',
        to: '/tasks/'
    },], [{
        label: 'Kijelentkezés',
        icon: 'i-heroicons-arrow-left-on-rectangle',
        click: () => {
            logout();
        }
    }]
]

const user = useSupabaseUser();
const client = useSupabaseClient();
const router = useRouter();

async function logout() {
    try {
        const { error } = await client.auth.signOut();
        if (error) throw error;
        router.push("/login");
    } catch (error) {
        console.log(error.message);
    }
}
</script>