<template lang="">
    <h1>List of Posts</h1>
    <div v-for="post in posts" :key="post.id">
        <OnePost :post="post"/>    
    </div>
</template>
<script>
import { ref } from 'vue'
import OnePost from '../components/OnePost.vue'
export default {
    components: { OnePost },
    setup() {
        const posts = ref([
            {
                "id": 1,
                "title": "Learn Angular",
                "content": "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Obcaecati, quibusdam."
            },
            {
                "id": 2,
                "title": "Learn React",
                "content": "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Obcaecati, quibusdam."
            },
            {
                "id": 3,
                "title": "Learn Spring Boot",
                "content": "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Obcaecati, quibusdam."
            }
        ])

        return { posts }
    }
}
</script>
<style lang="">
    
</style>