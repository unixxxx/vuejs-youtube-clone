<template>
    <div>
        <ul class="list-group">
            <li v-for="video in videos" :key="video.etag" class="list-group-item media" @click="videoSelect(video)">
                <video-list-item :video="video"></video-list-item>
            </li>
        </ul>
    </div>
</template>


<script>
import VideoListItem from './VideoListItem';

export default {
    name: 'VideoList',
    props: ['videos'],
    components: {VideoListItem},
    methods: {
        videoSelect(video) {
            this.$emit('videoSelect', video);
        }
    }
}
</script>

<style scoped>
    li {
        cursor: pointer;
    }
    li:hover, li:active {
        background-color: #eee;
    }
</style>

