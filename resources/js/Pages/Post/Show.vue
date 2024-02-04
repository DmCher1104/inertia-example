<template>

        <h1 class=" border-b border-gray-900/10 text-lg pb-3 mb-3">Show</h1>
        <div class="mb-6">
            <Link :href="route('post.index')"
                  class="hover:bg-white hover:text-sky-500 block bg-sky-500 border border-sky-500 p-2 w-32 rounded-full text-center text-white">
                Back
            </Link>
        </div>
        <div v-if="post">
                <div>id:{{ post.id }}</div>
                <div>title:{{ post.title }}</div>
                <div>content:{{ post.content }}</div>
                <div class="text-right">{{ post.updated_at }}</div>
        </div>
</template>

<script>
import {Link} from '@inertiajs/vue3';
import MainLayout from "@/Layouts/MainLayout.vue";

export default {
    name: "Show",
    layout: MainLayout,
    components: {
        Link
    },
    props: ['post']
}
</script>

<style scoped>

</style>
