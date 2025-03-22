<script setup lang="ts">
import Box from './components/Box.vue';
import EuropeanPaymentCodeRenderer from './components/EuropeanPaymentCodeRenderer.vue';
import { ref } from 'vue';
const showtext = ref(false)
</script>

<template>
    <div class="grow bg-gray-200 p-8">
        <Box class="self-start w-fit">
            <div class="w-[320px]">
                <EuropeanPaymentCodeRenderer :code="{
                    iban: 'DE89370400440532013000',
                    name: 'Max Mustermann',
                    amount: 123.45,
                    text: 'RF18539007547034'
                }" :showtext="showtext"/>
            </div>
            <button @click="showtext = !showtext" class="mt-4">Toggle Text</button>
        </Box>
    </div>
</template>
