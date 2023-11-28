<script setup>
    const props = defineProps({
        title: {
            type: String,
            default: ""
        },
        enTitle: {
            type: String,
            default: ""
        }
    })

</script>

<template>
   <div class="mainTitle_box">
        <p class="chinese">{{ title }}</p>
        <p class="en">{{ enTitle }}</p>
    </div>
</template>

<style lang="scss">
    
</style>

