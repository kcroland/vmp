<template>
  <div>
    <v-card class="ma-4" flat>
      <v-item-group>
        <v-container>
          <v-row class="justify-space-around">
            <v-col v-for="option in options" :key="option" cols="10" md="5">
              <v-item>
                <v-card
                  :color="report === option.report ? '#4caf50' : ''"
                  class="d-flex align-center"
                  dark
                  height="60"
                  @click="
                    report === option.report
                      ? (report = '')
                      : (report = option.report)
                  "
                >
                  <v-scroll-y-transition>
                    <div class="display-1 flex-grow-1 text-center">
                      {{ option.title }}
                    </div>
                  </v-scroll-y-transition>
                </v-card>
              </v-item>
            </v-col>
          </v-row>
        </v-container>
      </v-item-group>

      <v-divider class="mx-4 mb-5"></v-divider>

      <v-slide-y-reverse-transition>
        <div v-if="report === 'new' && !selected">
          <v-container>
            <v-row class="mx-5 headline">
              Please select a form based on the description
            </v-row>
          </v-container>
          <v-container v-for="type in forms" :key="type.title">
            <v-row class="mx-5">
              <v-col cols="6" md="4">
                <v-icon large>{{ type.icon }}</v-icon>
                <v-btn
                  rounded
                  class="mx-3"
                  width="250px"
                  color="primary"
                  @click="selected = type.title"
                  >{{ type.title }}
                </v-btn>
                <v-icon>mdi-arrow-right</v-icon>
              </v-col>

              <v-col cols="12" md="8">
                <v-card class="pa-2" outlined tile>
                  {{ type.use }}
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </div>
      </v-slide-y-reverse-transition>

      <v-slide-y-reverse-transition>
        <v-container v-if="selected && report === 'new'">
          <v-btn @click="selected = ''">Return</v-btn>
        </v-container>
      </v-slide-y-reverse-transition>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "Forms",
  data: () => ({
    options: [
      {
        title: "Make New Request",
        report: "new"
      },
      {
        title: "Your Requests",
        report: "old"
      }
    ],
    // Add example reports ('Use this report if...') and images (ex. different kinds of signs or invasive species)
    forms: [
      {
        title: "Wildlife Sighting",
        icon: "mdi-paw",
        use: "...add a bird or other wildlife sighting to our database"
      },
      {
        title: "Trail Report",
        icon: "mdi-road-variant",
        use: "...poor trail condition or need for maintenance"
      },
      {
        title: "Encampment",
        icon: "mdi-tent",
        use: "...tents or other signs of unregistered living at the park"
      },
      {
        title: "Park Signs",
        icon: "mdi-routes",
        use: "...a park landmark or trail sign is found damaged"
      },
      {
        title: "Offleash Pets",
        icon: "mdi-dog-side",
        use: "...a dog is offleash with its owner"
      },
      {
        title: "Litter/Dumping",
        icon: "mdi-trash-can",
        use: "...there is a large area of trash"
      },
      {
        title: "Graffiti/Tagging",
        icon: "mdi-spray",
        use: "...spray paint marking on buildings or landmarks"
      },
      {
        title: "Vegetation Concerns",
        icon: "mdi-sprout",
        use: "...invasive species, fallen tree, damaged plants, etc."
      },
      {
        title: "Other Inquiry",
        icon: "mdi-comment-question",
        use: "...any other general comments or things to report"
      }
    ],
    selected: "",
    report: ""
  })
};
</script>

<style scoped>

</style>
