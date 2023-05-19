<template>
    <div class="app">
        <!-- 
            props: src="https://im-awesome.me/your-awesome-image.jpg"
        -->
        {{ src }}
        <hr />
        {{ test }} 
        <ImageSrc v-model:modelValue="src" v-model:testInput="test" @handleClick="handleClick"/>
        
        <input type="range" />

        <MagnifierImage :src="src" />
    </div>
</template>

<script setup>
import { ref } from 'vue';
import MagnifierImage from './components/MagnifierImage.vue';
import ImageSrc from './components/ImageSrc.vue';

const src = ref('https://images.pexels.com/photos/4175000/pexels-photo-4175000.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1');

const test = ref('');

const handleClick = (e) => {
    console.log('parent click', e)
}


</script>

<style scoped>
.img-src {
    width: 85%;
    margin-bottom: 20px;
    padding: 20px;
    border: 1px solid #e6e6e6;
    border-radius: 5px;
}
</style>