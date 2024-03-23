<script setup lang="ts">
import logo from './assets/logoFull-removebg.png'
import blogForm from './components/blogForm.vue'
// import {mdiArrowRight} from '@mdi/font'
// icon="mdi-arrow-right" icon="mdi-arrow-left"
</script>

<template>
  <v-sheet class="d-flex flex-wrap" style="background: transparent;"> 
    <v-sheet class="flex-1-0 ma-2 pa-2" style="background: transparent;">
      <!-- Header -->
      <header >
        <v-container class="mx-0" fixed>
          <div>
            <img :src="logo" alt="Logo" />
          </div>
        </v-container>
      </header>

      <!-- Blog Content -->
          <v-card>
            <span>Blog posts to go here!</span>
            <v-card-actions class="d-flex justify-space-between">
              <v-btn  rounded color="green-darken-1" variant="outlined">Back</v-btn>
              <v-btn rounded color="green-darken-3" variant="outlined">Next</v-btn>
            </v-card-actions>
          </v-card>
    </v-sheet>
  </v-sheet>

  <!-- Blog Form -->
  <v-container class="d-flex flex-row fixed">
    <v-row>
      <v-col>
        <blogForm />
      </v-col>
    </v-row>
  </v-container>
</template>
