<template>
  <v-card class="ma-4" flat>
    <v-card-title class="headline">
      Discovery Park Maps
    </v-card-title>
    <v-card-text>
      <v-container fluid>
        <v-row>
          <v-col cols="12">
            <v-row
              class="justify-center"
              style="height: 100px;"
            >
              <v-card
                v-for="map in maps"
                :key="map.name"
                class="ma-3 pa-6"
                @click="mapsrc = map.src"
              >
                {{ map.name }}
              </v-card>
            </v-row>
          </v-col>
        </v-row>
      </v-container>

      <h1 v-if="!mapsrc" class="text-center ma-10">Please select a map.</h1>

      <iframe
        v-if="mapsrc"
        width="100%"
        height="640px"
        :src="mapsrc.length > 0 ? mapsrc : ''"
        frameborder="0"
        scrolling="yes"
      ></iframe>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: 'Maps',
  data: () => ({
    mapsrc: "",
    maps: [
      {
        name: "Ecosystem Affordances",
        src: "https://fodp.maps.arcgis.com/apps/MapJournal/index.html?appid=6f9efcf8e02547b39e576f484e04268d"
      },
      {
        name: "Public Information",
        src: "http://www.arcgis.com/apps/PublicInformation/index.html?appid=84db64c7f275403daa76ed56e168c670"
      },
      {
        name: "History of Discovery Park",
        src: "https://fodp.maps.arcgis.com/apps/Cascade/index.html?appid=7553f1fb519c455ca1c5af872f37bc7a"
      }
    ]
  }),
}
</script>