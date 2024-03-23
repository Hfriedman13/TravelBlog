<script setup lang="ts">
import { ref } from 'vue'
import textInput from './textInput.vue'

const weather = ['Sunny', 'Cloudy', 'Rainy', 'Snowy', 'Windy'] // can think of more idk.
const selected = ref(false)
const showDatePicker = ref(false)
const selectedDate = ref(null)

function toggleDatePicker(): void {
    showDatePicker.value = !showDatePicker.value
} 
</script>

<template>
  <!-- this meeds to be as wide as the page-->
  <v-form class="pa-10" variant="outlined">
    <v-container>
      <textInput label="CampGround" placeholder="Ramblin Redwoods" inputType="text" />
      <v-row>
        <v-col cols="12" md="6">
          <textInput label="Location" placeholder="Crecent City, CA" inputType="text" />
        </v-col>
        <v-col cols="12" md="6">
          <textInput label="Phone Number" placeholder="123-456-7890" inputType="number" />
        </v-col>
      </v-row>
<v-row>
     <v-col>
          <v-btn @click="toggleDatePicker">Select Date</v-btn>
          <v-date-picker v-model="selectedDate" color="primary" :show-week="true" v-if="showDatePicker"></v-date-picker>
          <v-text-field v-model="selectedDate" label="Selected Date" readonly></v-text-field>
        </v-col>
      </v-row>
      <!-- <v-date-picker color="primary" :show-week="true"></v-date-picker> -->
      <!--need to have a save or field where the date goes -->
      <v-select class="py-4" label="Weather" :items="weather" />
      <!-- insert icons -->
      <v-row>
        <v-col cols="12" md="6">
          <textInput label="Site #" />
        </v-col>

        <v-col cols="12" md="6">
          <textInput label="Ideal Site #(s)" />
        </v-col>
      </v-row>

      <!-- make reusable component for text areas-->
      <v-checkbox v-model="selected" label="Meet people?" value="true" />
      <div v-if="selected">
        <textInput label="Who did we meet?" />
      </div>
      <v-textarea label="Offerings" clearable variant="outlined" />
      <v-textarea label="Places Visited" clearable variant="outlined"></v-textarea>
      <v-textarea label="What we enjoyed most" clearable variant="outlined"></v-textarea>
      <v-textarea label="Most Memorable Moment" clearable variant="outlined"></v-textarea>
      <v-textarea
        label="Places to remember for next time"
        clearable
        variant="outlined"
      ></v-textarea>
      <v-textarea label="Additional comments..." clearable variant="outlined"></v-textarea>
    </v-container>
  </v-form>
</template>
