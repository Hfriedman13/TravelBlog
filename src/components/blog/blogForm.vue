<script setup lang="ts">
import { ref } from 'vue'
import textInput from '@/components/inputs/textInput.vue'
import saveBtn from '../buttons/saveBtn.vue';

interface FormData {
    campground: string;
    location: string;
    phoneNumber: string;
    selectedDate: Date | null;
    weather: string;
    siteNumber: string;
    idealSiteNumbers: string;
    meetPeople: boolean;
    whoDidWeMeet?: string;
    offerings: string;
    placesVisited: string;
    enjoyedMost: string;
    memorableMoment: string;
    placesToRemember: string;
    additionalComments: string;
}

const weather = ['Sunny', 'Cloudy', 'Rainy', 'Snowy', 'Windy'] // can think of more idk.
const selected = ref(false)
const showDatePicker = ref(false)
const selectedDate = ref(null)
const formData = ref<FormData>();

function toggleDatePicker(): void {
  showDatePicker.value = !showDatePicker.value
}

const saveFormData = (data: any) => {
    formData.value = data.value;
    console.log(data) // undefined
};
</script>

<template>
  <!-- this meeds to be as wide as the page-->
  <v-card variant="outlined">
    <v-form class="d-flex align-center">
      <v-container class="ma-10">
        <textInput label="CampGround" placeholder="Ramblin Redwoods" inputType="text" />
        <v-row>
          <v-col cols="12" md="6">
            <textInput label="Location" placeholder="Crecent City, CA" inputType="text" />
          </v-col>
          <v-col cols="12" md="6">
            <textInput label="Phone Number" placeholder="123-456-7890"/>
          </v-col>
        </v-row>
        <v-row>
          <v-col style="display: flex; justify-content: space-between">
            <v-btn @click="toggleDatePicker">Select Date</v-btn>
            <v-date-picker
              v-model="selectedDate"
              color="primary"
              :show-week="true"
              v-if="showDatePicker"
            ></v-date-picker>
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
    <v-card-actions class="float-right">
        <saveBtn @save="saveFormData"/>
      </v-card-actions>
  </v-card>
</template>
