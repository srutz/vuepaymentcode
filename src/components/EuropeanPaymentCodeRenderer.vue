<template>
    <img style="width: 100%; height: auto;" v-if="url" :src="url" :alt="url" />
    <pre v-if="showtext" style="font-size: 0.75rem">{{ content.map((l,i) => i.toString().padStart(2, "0") + " " + l).join('\n') }}</pre>
</template>
<script setup lang="ts">

/*
 * Render a European Payment Code as a QR code
 *
 * @see https://de.wikipedia.org/wiki/EPC-QR-Code
 * @see https://en.wikipedia.org/wiki/EPC_QR_code
 * 
 * @æuthor: stepan rutz
 */

import { onMounted, ref } from 'vue'
import QRCode from "qrcode";

export type EuropeanPaymentCode = {
    iban: string
    name: string
    amount: number
    text: string
}

const { code } = defineProps<{
    code: EuropeanPaymentCode
    showtext?: boolean // for debugging
}>()


const nf = new Intl.NumberFormat('en-US', { style: 'decimal', currency: 'EUR' })

function formatAmount(amount: number) {
    return nf.format(amount)
}

function formatLeadingZeroes(str: string) {
    return str.padStart(2, '0')
}

function limitString(str: string, limit: number) {
    return str.length > limit ? str.slice(0, limit) : str
}

const content = [
    "BCD",
    "002",
    "1",
    "SCT",
    "",
    limitString(code.name, 70),
    code.iban,
    "EUR" + formatAmount(code.amount),
    "",
    "",
    limitString(code.text, 140),
    ""
]
const url = ref("")

onMounted(async () => {
    url.value = await QRCode.toDataURL(content.join('\n'), { errorCorrectionLevel: 'H' })
})

</script>
