<template>
    <MainLayout>
        <h1 class="text-lg"> Posts </h1>
        <div class="mb-8">
            <Link :href="route('post.create')" class="hover:bg-white hover:text-sky-500 border border-sky-500
            block p-2 w-32 bg-sky-500 rounded-full text-center text-white "> Add Post
            </Link>
        </div>

        <div v-if="posts">
            <div class="mt-8 pt-8 border-t border-gray-300"
                 v-for="post in posts">
                <div> id: {{ post.id }}</div>
                <div> title: {{ post.title }}</div>
                <div> content: {{ post.content }}</div>
                <div class="text-sm text-right"> {{ post.date }}</div>
                <div class="text-sm text-right">
                    <Link class="text-sky-500" :href="route('post.show', post.id)"> Show </Link>
                </div>
                <div class="text-sm text-right">
                    <Link class="cursor-pointer text-sky-500" :href="route('post.edit', post.id)"> Edit </Link>
                </div>
                <div class="text-sm text-right">
                    <Link @click="deletePost(post.id)" class="text-red-500" > Delete </Link>
                </div>
            </div>
        </div>
    </MainLayout>
</template>

<script>

import {Link} from "@inertiajs/vue3";
import MainLayout from "@/Layouts/MainLayout.vue";

export default {
    name: "Index",

    props: [
        'posts'
    ],

    components: {
        Link,
        MainLayout
    },

    methods: {
        deletePost(id){
            this.$inertia.delete(`/posts/${id}`);
        }
    }
}


</script>
