<script lang="ts" setup>
    const authStore = useAuthStore();
    const isLoadingStore = useIsLoadingStore();
    const router = useRouter();

    const logout = async() => {
        isLoadingStore.set(true);
        await account.deleteSession('current');
        authStore.clear();
        await router.push('/login');
        isLoadingStore.set(false);
    }
</script>

<template>
    <aside class="px-5 py-8 bg-sidebar h-full relative w-full">
        <NuxtLink to="/">
            <NuxtImg src="./logo.svg" alt="" width="100px" class="mx-auto"></NuxtImg>
        </NuxtLink>

        <button class="absolute top-2 right-3 transition-colors hover:text-primary">
            <Icon @click="logout" name="line-md:logout" size="20"/>
        </button>

        <LayoutMenu class="mt-4"></LayoutMenu>
    </aside>
</template>