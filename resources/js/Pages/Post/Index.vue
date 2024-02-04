<template>
        <h1 class=" border-b border-gray-900/10 text-lg pb-3 mb-3">Posts</h1>
        <div class="mb-6">
            <Link :href="route('post.create')"
                  class="hover:bg-white hover:text-sky-500 block bg-sky-500 border border-sky-500 p-2 w-32 rounded-full text-center text-white">
                Add post
            </Link>
        </div>
        <div v-if="posts">
            <div v-for="post in posts" :key="post.id" class=",t-8 pt-8 border-t border-gray-300">
                <div>id:{{ post.id }}</div>
                <div>title:{{ post.title }}</div>
                <div>content:{{ post.content }}</div>
                <div class="text-right">{{ post.updated_at }}</div>
                <div class="text-right">
                    <Link class="text-sky-500" :href="route('post.show', post.id)">show</Link>
                </div>
                <div class="text-right">
                    <Link class="text-sky-500" :href="route('post.edit', post.id)">edit</Link>
                </div>
                <div class="text-right">
                    <p @click="deletePost(post.id)" class="cursor-pointer text-red-500" >delete</p>
                </div>
            </div>
        </div>
</template>

<script>
import {Link} from '@inertiajs/vue3';
import MainLayout from "@/Layouts/MainLayout.vue";

export default {
    name: "Index",
    layout: MainLayout,
    components: {
        Link
    },
    props: ['posts'],
    methods: {
        deletePost(id){
            this.$inertia.delete(`/posts/${id}`);
        }
    }
}
</script>

<style scoped>

</style>
