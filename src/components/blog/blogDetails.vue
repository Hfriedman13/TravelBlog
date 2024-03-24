<script setup lang="ts">
import { ref } from 'vue';

const props = defineProps({
  formData: Object // eventually create the object
});
</script>

<template>
  <v-card class="pa-10">
    <!-- Display form data here -->
    <div v-if="formData">
      <p>Campground: {{ formData.campground }}</p>
      <p>Location: {{ formData.location }}</p>
      
    </div>
  </v-card>
  <v-card-actions class="d-flex justify-space-between">
    <v-btn rounded color="green-darken-1" variant="outlined">Back</v-btn>
    <v-btn rounded color="green-darken-3" variant="outlined">Next</v-btn>
  </v-card-actions>
</template>
