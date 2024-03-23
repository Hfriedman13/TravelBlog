<script setup lang="ts">
import { ref } from 'vue';

const travelPlaces = ref([
    { title: 'Moab, Utah', date: '04-01-2024', images: [{ src: 'url1', caption: 'Caption 1' }] },
    { title: 'Ririe, Idaho', date: '2022-02-01', images: [{ src: 'url2', caption: 'Caption 2' }] },
    { title: 'Caption 1', date: '2022-02-01', images: [{ src: 'url2', caption: 'Caption 2' }] },
    { title: 'Caption 2', date: '2022-02-01', images: [{ src: 'url2', caption: 'Caption 2' }] },
    { title: 'Caption 3', date: '2022-02-01', images: [{ src: 'url2', caption: 'Caption 2' }] },
    { title: 'Caption 4', date: '2022-02-01', images: [{ src: 'url2', caption: 'Caption 2' }] },
    { title: 'Caption 5', date: '2022-02-01', images: [{ src: 'url2', caption: 'Caption 2' }] },
    // Add more places as needed
]);

const selectedPlace = ref<{ title: string; date: string; images: { src: string; caption: string }[] } | null>(null);
const showDetails = ref(false);

const expandView = (place: { title: string; date: string; images: { src: string; caption: string }[] }) => {
  selectedPlace.value = place;
  showDetails.value = true;
};

const closeDetails = () => {
  showDetails.value = false;
};
</script>


<template>
  <div>
    <v-container>
      <v-row>
        <v-col>
          <v-timeline>
            <v-timeline-item v-for="(place, index) in travelPlaces" :key="index">
              <v-timeline-item-icon>
                <v-icon>mdi-map-marker</v-icon>
              </v-timeline-item-icon>
              <v-timeline-item-content>
                <v-row>
                  <v-col>
                    <h3>{{ place.title }}</h3>
                    <p>{{ place.date }}</p>
                    <!-- Trigger the details view -->
                    <v-btn @click="expandView(place)">View Pictures</v-btn>
                  </v-col>
                </v-row>
              </v-timeline-item-content>
            </v-timeline-item>
          </v-timeline>
        </v-col>
      </v-row>
    </v-container>

    <!-- Details View -->
    <PictureCarousel :selectedPlace="selectedPlace" :showDetails="showDetails" @closeDetails="closeDetails" />
  </div>
</template>

