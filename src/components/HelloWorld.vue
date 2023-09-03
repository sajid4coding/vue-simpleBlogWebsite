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
</script>

<template>
    <template v-for="(post, index) in postList" :key="index">
        <h2>{{ post.title.rendered }}</h2>
        <small>{{ post.date }}</small>
        <p>{{ post.content.rendered }}</p>
    </template>
</template>
