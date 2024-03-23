<script setup lang="ts">
import titlePage from './components/titlePage.vue'
// import timeline from './components/homeTimeLine.vue'
import blogForm from './components/blogForm.vue';
</script>

<template>
  <div>
    <!-- fix eventually -->
    <header style="position: fixed; top: 0; left: 0; width: 25%; z-index: 1000">
      <v-container class="mx-0" fixed>
        <div>
          <titlePage msg="Welcome to Our Blog!" />
        </div>
      </v-container>
    </header>
  </div>

  <v-container class="d-flex flex-row fixed">
    <v-row>
      <v-col>
       <blogForm/>
      </v-col>
    </v-row>
  </v-container>
</template>
