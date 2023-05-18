<template>
    <div class="magnifier-image">
        <div 
            v-if="magnifier.showMagnifier"
            :style="{
                height: `${magnifier.magnifierHeight}px`,
                width: `${magnifier.magnifierWidth}px`,
                top: `${magnifier.y - magnifier.magnifierHeight / 2}px`,
                left: `${magnifier.x - magnifier.magnifierWidth / 2}px`,
                backgroundImage: `url(${src})`,
                backgroundSize: `${magnifier.sizeWidth * magnifier.zoomLevel}px ${
                    magnifier.sizeHeight * magnifier.zoomLevel
                }px`,
                backgroundPositionX: `${-magnifier.x * magnifier.zoomLevel + magnifier.magnifierWidth / 2}px`,
                backgroundPositionY: `${-magnifier.y * magnifier.zoomLevel + magnifier.magnifierHeight / 2}px`,
                pointerEvents: `${magnifier.pointerEvents}`
            }" 
            class="zoom-image">
        </div>
        <img 
            :src="src"
            @mouseenter="setSize"
            @mousemove="setXY"
            @mouseleave="magnifier.showMagnifier = false"
            @wheel="adjustZoom($event)"
        />
    </div>
</template>

<script setup>
import { ref } from 'vue';

const { src } = defineProps({
    src: {
        type: String
    }
})

const magnifier = ref({
    x: 0,
    y: 0,
    magnifierWidth: 100,
    magnifierHeight: 100,
    sizeWidth: 0,
    sizeHeight: 0,
    showMagnifier: false,
    zoomLevel: 2,
    pointerEvents: "none"
})

const setSize = (e) => {
    const elem = e.currentTarget;
    const { width, height } = elem.getBoundingClientRect();
    magnifier.value.sizeWidth = width;
    magnifier.value.sizeHeight = height;
    magnifier.value.showMagnifier = true;
}

const setXY = (e) => {
    const elem = e || window.event;
    magnifier.value.x = elem.offsetX;
    magnifier.value.y = elem.offsetY;
    //console.log(magnifier.value.x)
}

const adjustZoom = (e) => {
    const { deltaY } = e;
    let zoomLevel;

    if(deltaY > 0) {
        zoomLevel = magnifier.value.zoomLevel + 0.5;
    } else if (deltaY < 0) {
        zoomLevel = magnifier.value.zoomLevel - 0.5;
    }

    magnifier.value.zoomLevel = zoomLevel;
}
</script>

<style scoped>
.magnifier-image {
    position: relative;
    width: 300px;
    overflow: hidden;
}

.magnifier-image img {
    width: 100%;
}

.zoom-image {
    position: absolute;
    width: 100px;
    height: 100px;
    background-repeat: no-repeat;
    background-color: transparent;
    border-radius: 50%;
}
</style>