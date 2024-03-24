<script setup lang="ts">
import { defineEmits } from 'vue';

const emits = defineEmits(['save']);
const saveForm = () => {
    // Here you can gather the form data and emit it to the parent component
    emits('save', /* pass form data */);
};
</script>

<template>
    <v-btn variant="outlined" @click="saveForm">Save</v-btn>
</template>