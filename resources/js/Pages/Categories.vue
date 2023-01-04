<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import { Head, useForm } from "@inertiajs/inertia-vue3";

defineProps({
    categories: [],
});

const form = useForm({
    title: "",
});

function addCategory() {
    form.post(route("categories.store"), {
        onFinish: () => {
            form.title = "";
        },
    });
}

function deleteCategory(id) {
    if (!confirm("are you sure?")) return;
    useForm().delete(route("categories.destroy", { category: id }));
}
</script>

<template>
    <Head title="Categories" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Categories
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div
                    class="bg-white m-2 p-2 overflow-hidden shadow-sm sm:rounded-lg"
                >
                    <div>
                        <h1 class="p-2 font-bold">Add a new categorie:</h1>
                        <!-- {{categories}} -->
                        <form v-on:submit.prevent="addCategory()">
                            <input
                                type="text"
                                placeholder="title"
                                v-model="form.title"
                                class="m-2 p-2 rounded bg-grey-100"
                            />
                            <button
                                class="m-2 p-2 font-bold rounded bg-blue-100"
                            >
                                Add
                            </button>
                            <h1 class="p-2 font-bold">All categories:</h1>
                        </form>

                        <ul>
                            <li
                                v-for="categorie of categories"
                                :key="categorie"
                                class="m-2 p-2 rounded bg-blue-100"
                            >
                                {{ categorie.title }}
                                <a
                                    class="cursor-pointer font-bold text-red-500 m-2 p-2"
                                    v-on:click="deleteCategory(categorie.id)"
                                    >&times;</a
                                >
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
