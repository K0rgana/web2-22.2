<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import { Head, useForm, Link } from "@inertiajs/inertia-vue3";
import Button from "@/Components/PrimaryButton.vue";

const props = defineProps({
    products: {
        type: Object,
        default: () => ({}),
    },
    category: [],
});

const form = useForm({
    title: "",
    status: "",
    category: [],
    description: "",
});

const submit = () => {
    form.post(route("products.store"));
};
</script>

<template>
    <Head title="Product Create" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="text-xl font-semibold leading-tight text-gray-800">
                Product Create
            </h2>
        </template>

        <div class="py-12">
            <div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
                <div class="overflow-hidden bg-white shadow-sm sm:rounded-lg">
                    <div class="p-6 bg-white border-b border-gray-200">
                        <form @submit.prevent="submit">
                            <div class="mb-6">
                                <label for="Title" class="block mb-2"
                                    >Title</label
                                >
                                <input
                                    type="text"
                                    v-model="form.title"
                                    name="title"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
                                    placeholder=""
                                />
                                <div
                                    v-if="form.errors.title"
                                    class="text-sm text-red-600"
                                >
                                    {{ form.errors.title }}
                                </div>
                            </div>
                            <div class="mb-6">
                                <label for="status" class="block">Status</label>
                                 <select
                                    v-model="form.status"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full"
                                >
                                    <option value="Pending">Pending</option>
                                    <option value="In progress">
                                        In progress
                                    </option>
                                    <option value="Completed">Completed</option>
                                    <option value="Quit">Quit</option>
                                </select>

                                <div
                                    v-if="form.errors.status"
                                    class="text-sm text-red-600"
                                >
                                    {{ form.errors.status }}
                                </div>
                            </div>
                            <div class="mb-6">
                                <label for="category" class="block"
                                    >Category</label
                                >
                                <!--  <select
                                    v-model="form.category"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full"
                                >
                                    <option
                                        v-for="category in categories"
                                        :value="category"
                                    >
                                        {{ category.title }}
                                    </option>
                                </select>
                                <div
                                    v-if="form.errors.status"
                                    class="text-sm text-red-600"
                                >
                                    {{ form.errors.status }}
                                </div> -->
                            </div>
                            <div class="mb-6">
                                <label for="status" class="block mb-2"
                                    >Description</label
                                >
                                <textarea
                                    type="text"
                                    v-model="form.description"
                                    name="description"
                                    id=""
                                    class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
                                ></textarea>

                                <div
                                    v-if="form.errors.description"
                                    class="text-sm text-red-600"
                                >
                                    {{ form.errors.description }}
                                </div>
                            </div>
                            <Button
                                type="submit"
                                class="text-white bg-blue-700 focus:outline-none font-medium rounded-lg text-sm px-5 py-2.5"
                                :disabled="form.processing"
                                :class="{ 'opacity-25': form.processing }"
                            >
                                Submit
                            </Button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
