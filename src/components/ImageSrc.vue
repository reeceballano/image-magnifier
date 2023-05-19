<template>
    <div class="image-src">
        <input 
            :value="modelValue" 
            @input="$emit('update:modelValue', $event.target.value)"
            type="text" 
            class="img-src"
        />

        <input type="text" :value="testInput" @input="$emit('update:testInput', $event.target.value)" />

        <button @click="handleClick()">click</button>
    </div>
</template>

<script setup>
const props = defineProps({
    modelValue: {
        type: String,
        default: 'https://images.pexels.com/photos/4175000/pexels-photo-4175000.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1'
    },
    testInput: {
        type: String
    }
})

const emit = defineEmits(['handleClick'])

const data = [props.modelValue, props.testInput]
const handleClick = () => {
    console.log('child click', props)
    emit('handleClick', props);
}
</script>
