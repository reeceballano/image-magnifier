<template>
    <div class="app">
        <!-- 
            props: src="https://im-awesome.me/your-awesome-image.jpg"
        -->
        <input 
            v-model="imgSrc" 
            type="text" 
            class="img-src"
        />

        <MagnifierImage :src="imgSrc" />
    </div>
</template>

<script setup>
import { ref } from 'vue';
import MagnifierImage from './components/MagnifierImage.vue';

const imgSrc = ref('https://images.pexels.com/photos/4175000/pexels-photo-4175000.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1');
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