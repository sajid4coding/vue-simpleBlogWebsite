<script setup>
    import axios from 'axios';
    import { ref } from 'vue';

    let postList = ref(null);

    async function getPostList(){
        let url="https://mehedipata.com/wp-json/wp/v2/posts";
        let res=await axios.get(url);
        postList.value=res.data
    }
    getPostList()


    let categories = ref(null);

    async function getCategories(){
        let url="https://mehedipata.com/wp-json/wp/v2/categories";
        let res=await axios.get(url);
        categories.value=res.data
    }
    getCategories()
</script>

<template>
    <div class="row">
        <div class="col-8">
            <h2 class="mb-4">Blog Lists</h2>
            <template v-for="(post, index) in postList" :key="index">
                <h4>Title: {{ post.title.rendered }}</h4>
                <h6 class="text-center my-4">Date: {{ post.date }}</h6>
                <p v-html="post.content.rendered"></p>
                <hr class="mb-5">
            </template>
        </div>
        <div class="col-4">
            <h2 class="mb-4">Categories</h2>
            <template v-for="(category, index) in categories" :key="index">
                <h4>{{ category.name }}</h4>
            </template>
        </div>
    </div>
</template>
