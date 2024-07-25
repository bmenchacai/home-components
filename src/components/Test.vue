<template>
    <div class="relative w-full">
        <label for="tipoDocumento" class="block mb-1 text-sm font-medium text-gray-700">Importe Carta autorización*</label>
        <div class="flex items-center">
            <label for="amount"
                class="bg-gray-200 text-gray-700 px-3 py-2 border border-r-0 border-gray-300 rounded-l-md"
                style="background-color: white; height: 38px !important;">$</label>
            <input type="text" id="amount" v-model="formattedAmount" @input="formatCurrency"
                :class="{'border-red-500': form.amountError, 'border-gray-300': !form.amountError}"
                placeholder="00.00"
                class="border-gray-300 focus:ring-gray-300 block w-full px-3 py-2 sm:text-sm border rounded-r-md">
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { defineProps } from 'vue';
import currency from 'currency.js';

defineProps({
    msg: String,
});

const form = reactive({
    amount: '',
    amountError: false,
});

const formattedAmount = computed(() => {
    let value = form.amount.replace(/[^\d.]/g, '');
    if (!isNaN(value) && value.split('.').length <= 2) {
        let formattedValue = currency(value, { separator: ',', precision: 2 }).format();
        return formattedValue;
    } else {
        return '';
    }
});

function formatCurrency(event) {
    // Update reactive form data
    form.amount = event.target.value;
}
</script>
