<template>
    <div class="app">
        <!-- 
            props: src="https://im-awesome.me/your-awesome-image.jpg"
        -->
        <ImgSrc v-model:imgSrc="imgSrc" />

        <Suspense>
            <template #default>
                <MagnifierImage :src="imgSrc" />
            </template>

            <template #fallback>
                <h2>Loading...</h2>
            </template>
        </Suspense>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import MagnifierImage from './components/MagnifierImage.vue';
import ImgSrc from './components/ImgSrc.vue';

const imgSrc = ref('https://images.pexels.com/photos/4175000/pexels-photo-4175000.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1');
</script>

