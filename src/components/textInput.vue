<script setup lang="ts">

defineProps({
    label: {
        type: String,
        default: ""
    },
    placeholder: {
        type: String,
        default: ""
    },
    inputType: {
         type: String,
        default: "input"
    }
})

</script>

<template>
    <v-text-field :label="label" :placeholder="placeholder" :type="inputType"></v-text-field>
</template>