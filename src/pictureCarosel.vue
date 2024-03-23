<script setup lang="ts">
import { ref, defineProps } from 'vue';

const { selectedPlace, showDetails } = defineProps(['selectedPlace', 'showDetails']);
</script>

<template>
  <v-dialog v-model="showDetails.value" max-width="600px">
    <v-row>
      <v-col>
        <!-- Picture Carousel -->
        <v-carousel>
          <v-carousel-item v-for="(image, i) in selectedPlace?.images" :key="i">
            <img :src="image.src" :alt="image.caption">
            <v-carousel-item-caption>{{ image.caption }}</v-carousel-item-caption>
          </v-carousel-item>
        </v-carousel>
      </v-col>
      <v-col>
        <!-- Blog Post Section -->
        <v-card>
          <v-card-title>{{ selectedPlace?.title }}</v-card-title>
          <v-card-text>
            <!-- Add your blog post content here -->
            <!-- <textarea v-model="selectedPlace?.blogPost" rows="10" cols="30" placeholder="Write your blog post..."></textarea> -->
          </v-card-text>
          <v-card-actions>
            <v-btn @click="$emit('closeDetails')">Close</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-dialog>
</template>
