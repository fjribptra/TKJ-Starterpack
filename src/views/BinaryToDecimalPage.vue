<template>
    <div class="flex flex-col gap-3 py-4 px-6">
        <h1 class="font-bold">Binary to decimal</h1>
        <div class="flex flex-col gap-3">
            <label for="binary">Binary 8 digits :</label>
            <input v-model="binary" class="border border-black p-2" :maxlength="8" type="text" @input="onInput" placeholder="Enter binary ( only 0 and 1 )">
            <label for="decimal">Decimal :</label>
            <input v-model="decimal" class="border border-black p-2" type="text" placeholder="Result" readonly>
        </div>
        <button class="bg-black text-white w-fit p-3 rounded-md" @click="onConvert">Convert</button>
    </div>
</template>

<script>
import { ref } from 'vue';
export default {
    name : 'BinaryToDecimalPage',
    setup() {
        const binary = ref('');
        const decimal = ref('');

        function onInput(event) {
            binary.value = event.target.value.replace(/[^01]/g, '');
        }

        function onConvert() {
            decimal.value = parseInt(binary.value, 2);
        }
        return {
            binary,
            decimal,
            onInput,
            onConvert
        }
    }
}
   
</script>