<template>
    <MainLayout>
        <h1 class="text-lg"> Edit </h1>
        <div class="mb-2">
            <Link :href="route('post.index')" class=" text-sm text-sky-500 mb-8">Back</Link>
        </div>

        <form @submit.prevent="update">
            <div class="mb-4">
                <input v-model="title" class="w-full rounded-full border-gray-300" type="text" placeholder="title">
            </div>
            <div class="mb-4">
                <textarea v-model="content" class="w-full rounded-full border-gray-300"
                          placeholder="content"> </textarea>
            </div>
            <div class="mb-4">
                <button class="hover:bg-white hover:text-sky-500 border border-sky-500
            block p-2 w-32 bg-sky-500 rounded-full text-center text-white ml-auto" type="submit"> Update
                </button>
            </div>
        </form>
    </MainLayout>
</template>

<script>
import {Link} from "@inertiajs/vue3";
import MainLayout from "@/Layouts/MainLayout.vue";

export default {


    name: "Create",

    props: [
      'post'
    ],


    data() {
        return {
            id: this.post.id,
            title: this.post.title,
            content: this.post.content,        }
    },

    methods: {
        update() {
           // console.log(this.title);
          this.$inertia.patch(`/posts/${this.id}`, {title: this.title, content: this.content})
        }
    },

    components: {
        Link,
        MainLayout
    }

}

</script>
