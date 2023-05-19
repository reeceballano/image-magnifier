<template>
    <div class="img-src">
        <input 
            :value="imgSrc" 
            @input="$emit('update:imgSrc', $event.target.value)"
            type="text" 
            class="img-src-input"
        />
    </div>
</template>

<script setup>
const { imgSrc } = defineProps({
    imgSrc: {
        type: String,
        default: 'https://images.pexels.com/photos/4175000/pexels-photo-4175000.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1'
    }
})
</script>

<style scoped>
.img-src-input {
    width: 85%;
    margin-bottom: 20px;
    padding: 20px;
    border: 1px solid #e6e6e6;
    border-radius: 5px;
}
</style>