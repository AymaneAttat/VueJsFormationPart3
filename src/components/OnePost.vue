<template lang="">
    <h2 @click="show = !show">{{post.title}} </h2>
    <p v-if="show">{{extract}} </p>
</template>
<script>
import { computed, ref, onMounted, onUpdated, onUnmounted } from 'vue'
export default {
    props: ['post'],
    setup(props){
        //Life cycle hooks
        onUnmounted(() => {
            console.log('One Post Unmounted')
        })
        onMounted(() => {
            console.log('One Post Mounted')
        })
        onUpdated(() => {
            console.log('One Post updated')
        })
        const show = ref(true)
        const extract = computed(() => props.post.content.substring(0, 50) + '...')

        return { extract, show }
    }
}
</script>
<style lang="">
    
</style>