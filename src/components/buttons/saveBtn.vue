<script setup lang="ts">
import { defineEmits } from 'vue';

const emits = defineEmits(['save']);

// eventually make universal not just save for form
const saveForm = (formData: FormData) => {
    emits('save',formData);
};
</script>

<template>
    <v-btn variant="outlined" @click="saveForm">Save</v-btn>
</template>