<template>
    <div class="flex">
        <img :src="thumbnailUrl" alt="video.snippet.title" class="mr-3">
        <div class="media-body">{{video.snippet.title}}</div>
    </div>
</template>

<script>
export default {
    name: 'VideoListItem',
    props: ['video'],
    computed: {
        thumbnailUrl() {
            return this.video.snippet.thumbnails.default.url;
        }
    }
}
</script>

<style scoped>
    .flex {
        display: flex;
    }
</style>


