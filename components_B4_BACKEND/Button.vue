<template>
    <button @click="onClick()" :style="{ background: color }" class="btn">{{ text }}</button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: String,
        color: String
    },
    methods: {
        onClick() {
            // console.log('Button clicked')
            // this.$emit('toggle-add-task')
            this.$emit('header-button-click')
        },
        
    },
    emits: ['header-button-click']
}
</script>

<style scoped>

</style>