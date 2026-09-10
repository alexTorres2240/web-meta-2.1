<script setup lang="ts">
import HolyCard from './components/HolyCard.vue'
import HolyHeader from './components/HolyHeader.vue'
import HolyFooter from './components/HolyFooter.vue'
</script>

<template>
  <v-app>
    <v-main>
      <HolyHeader titulo="HolyPortafolio"/>
      <v-container>
        <v-row>
          <v-col cols="12" md="6">
            <HolyCard
              imagen="https://picsum.photos/id/10/400/250"
              titulo="Paisaje"
              descripcion="Una fotografía obtenida mediante la API de Picsum."
              autor="Lorem Picsum"
            />
          </v-col>
          <v-col cols="12" md="6">
            <HolyCard
              imagen="https://picsum.photos/id/10/400/250"
              titulo="Paisaje"
              descripcion="Una fotografía obtenida mediante la API de Picsum."
              autor="Lorem Picsum"
            />
          </v-col>
        </v-row>
        <HolyFooter/>
      </v-container>
    </v-main>
  </v-app>
</template>