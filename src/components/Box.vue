<template>
    <div class="bg-white p-4 rounded-lg border border-gray-300 shadow-lg flex flex-col gap-2" :class="classes">
        <slot></slot>
    </div>
</template>
<script setup lang="ts">
import { defineProps } from 'vue'

defineProps({
    classes: {
        type: String,
        default: ''
    }
})

</script>

