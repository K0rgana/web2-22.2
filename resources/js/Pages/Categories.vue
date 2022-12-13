<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/inertia-vue3';

defineProps({
    'categories': []
})

</script>

<template>
    <Head title="Categories" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Categories</h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div>
                        <h1>categoriazinhas</h1>
                        <!-- {{categories}} -->
                        <ul>
                            <li class="m-2 p-2 rounded bg-blue-100">hello</li>
                            <li class="m-2 p-2 rounded bg-blue-100">hello</li>
                            <li v-for="categorie of categories" :key="categorie" class="p-2">
                                {{ categorie.title }} <a>&times;</a>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
