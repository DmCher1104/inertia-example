<template>
    <h1 class="border-b border-gray-900/10 text-lg pb-3 ">Edit post - {{ this.post.id }} form</h1>
    <form @submit.prevent="update">
        <div class="space-y-12">
            <div class="border-b border-gray-900/10 pb-6">
                <div class="mt-10 grid grid-cols-1 gap-x-6 gap-y-8 sm:grid-cols-6">
                    <div class="col-span-full">
                        <label for="title" class="block text-sm font-medium leading-6 text-gray-900">Title</label>
                        <div class="mt-2">
                            <div
                                class="flex rounded-md shadow-sm ring-1 ring-inset ring-gray-300 focus-within:ring-2 focus-within:ring-inset focus-within:ring-indigo-600 sm:max-w-md">
                                <span
                                    class="flex select-none items-center pl-3 text-gray-500 sm:text-sm">posts.com/</span>
                                <input
                                    v-model="title"
                                    type="text"
                                    name="title"
                                    id="title"
                                    autocomplete="title"
                                    class="block flex-1 border-0 bg-transparent py-1.5 pl-1 text-gray-900 placeholder:text-gray-400 focus:ring-0 sm:text-sm sm:leading-6"
                                    placeholder="your title">
                            </div>
                        </div>
                    </div>

                    <div class="col-span-full">
                        <label for="content" class="block text-sm font-medium leading-6 text-gray-900">Content</label>
                        <div class="mt-2">
                                <textarea
                                    v-model="content"
                                    id="content"
                                    name="content"
                                    rows="3"
                                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"></textarea>
                        </div>
                        <p class="mt-3 text-sm leading-6 text-gray-600">Write a few sentences.</p>
                    </div>
                </div>
            </div>
        </div>

        <div class="mt-6 flex items-center justify-end gap-x-6">
            <Link :href="route('post.index')" class="text-sm font-semibold leading-6 text-gray-900">Cancel (back)</Link>
            <button type="submit"
                    class="rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">
                Update
            </button>
        </div>
    </form>
</template>

<script>
import {Link} from '@inertiajs/vue3';
import MainLayout from "@/Layouts/MainLayout.vue";

export default {
    name: "Edit",
    layout: MainLayout,
    components: {
        Link
    },
    props: ['post'],
    data(){
        return {
            id: this.post.id,
            title: this.post.title,
            content: this.post.content
        }
    },
    methods: {
        update() {
            this.$inertia.patch(`/posts/${this.id}`, {title: this.title, content:this.content})
        }
    },
}
</script>

<style scoped>

</style>
